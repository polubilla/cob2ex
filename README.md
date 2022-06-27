# cob2ex
COBOL to Elixir translator. 
Work In Progress...

<!-- Un comentario -->
### Table of Content
* [Motivation](#motivation)  
* [Technical Analysis](#technical-analysis)  
* [Tools Analysis](#tools-analysis)  
* [Ecosystem](#ecosystem)  
* [General Considerations](#general-considerations)  
* [Miscelanous references](#misc-references)


## Motivation  
**COBOL**
* 70-80% of all business transactions worldwide are written in COBOL
* 60 million patients are cared for daily with COBOL programs
* 95% of all ATM transactions are processed using COBOL
* 96% of all vacations booked daily involve COBOL
* The Social Security Admin (USA) has 60 million lines of COBOL code
* The IRS(USA) has 50 million lines of COBOL code

*Three Key Findings*
1. **250 billion lines of COBOL in use** A large percentage in the financial industry.
2. **The future of COBOL** 58% of respondents were willing to admit that their COBOL applications will be sticking around for the next half decade or more.
3. **Skills challenge** There is a great shortage of programmers with Cobol skills.

_Ref_: [The Truth About COBOL and the World Economy.  By Reg Harbeck / July 19, 2021](https://techchannel.com/Trends/07/2021/survey-says-cobol)

#### Experiences
* When the Commonwealth Bank of Australia replaced its core COBOL platform in 2012, it took five years at a final cost of $750 million ($1 billion Australian).

* UK bank TSB was forced to migrate their COBOL systems due to a buyout in 2018, the bank was unable to trade in days, the cost of the migrating cost them 330 million pounds, that is not all, they also lost 49 million pounds from financial fraud while their systems were down. The bank had more than 200000 customer complaints, the chief executive had to resign.

---
**Elixir**  
Dynamic, functional language designed for building scalable and maintainable applications. Elixir leverages the Erlang VM, known for running low-latency, distributed and fault-tolerant systems, while also being successfully used in web development and the embedded software domain

## Technical Analysis  
Process description:

```mermaid
graph LR;    
    Code-OL-- Parsing -->AST-OL;
    AST-OL-- Transform1 -->InterModel;
    InterModel-- Transform2 -->AST-TL;
    AST-TL-- CodeGen -->Code-TL;
```

* **Stage 1: Scanning / Parsing**  
* * Input   : Code in the original language  
* * Process :   
* * * *Scanning* Consumes the plain text of the code file, group together individual characters to form tokens (lexer) 
* * * *Parsing* Consumes tokens and groups them together into complete statements and expression. The Parser is guided by a grammar
* * Output  : AST-OL::AST of the original language  

* **Stage 2: Transformation 1**
* * Input   : AST-OL
* * Process : *Semantic analysis* Traverse the AST-OL and derive additional meaning (semantis) about the program from the rules of the language and the relationship between elements of the program.
* * Output  : Intermediate Model
 
* **Stage 3: Transformation 2**
* * Input   : Intermediate Model 
* * Process : Convert the Intermediate Model (intermediate AST) into an AST of the target language
* * Output  : AST-TL::AST of the target language
 
* **Stage 4: Code generation**
* * Input   : AST-TL
* * Process : Convert the AST of the target language into valid *target language code*
* * Output  : Code in the target language

_Ref_ [How to write a transpiler - F.Tomassetti](https://tomassetti.me/how-to-write-a-transpiler/)


## Tools Analysis  

+ Lexers/Parsers
+ + Lex-Yacc
+ + Flex-Bison
+ + Leex-Yeec
+ ANTLR
+ Xtext

## Ecosystem   
<!-- "" Mainframes are around not just because of COBOL, but because of a whole ecosystem of things like Db2 and CICS. (CICS might be interesting to map to the BEAM model though..) -->

Cobol, RPG, JCL, CICS, DB2  


## General Considerations  
<!-- Introducción a las consideraciones generales. -->

"_COBOL bombs are not a problem because they are written in COBOL; they are a problem because the number of engineers who understand what they are doing well enough to maintain them is shrinking. Transpiling poorly documented, poorly organized COBOL into **Language** (i.e.:Java) just creates poorly documented, poorly organized, atypical Java code. The output of the transpiler is generally loaded with constructs and work arounds that are not intuitive to a good Java developer and may create hidden performance issues._" *M.Bellotti*
_Ref1_: [Defusing COBOL bombs with smart automation](https://medium.com/the-technical-archaeologist/defusing-cobol-bombs-with-smart-automation-9b24f81b5da4)

_Ref2_: [Why COBOL isn’t the problem](https://www.lucidchart.com/techblog/2020/11/13/why-cobol-isnt-the-problem/)  
_Ref3_: [COBOL Isn’t the issue: a misinterpreted crisis](https://hackaday.com/2020/04/20/cobol-isnt-the-issue-a-misinterpreted-crisis/)


## Misc References
[Implementing Domain-Specific Languages with Xtext and Xtend - Lorenzo Bettini](https://www.amazon.com/-/es/Lorenzo-Bettini/dp/1786464969)  

