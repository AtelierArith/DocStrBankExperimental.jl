```
ExpAndGram{T,N,A,B,C} <: AbstractExpAndGramAlgorithm
```

Non-adaptive algorithm of order N for computing the matrix exponential and an associated Gramian.

Constructor:

ExpAndGram{T,N}()

creates an algorithm with coefficients stored in the numeric type T of order N. Current supported values of N are 3, 5, 7, 9, 13.
