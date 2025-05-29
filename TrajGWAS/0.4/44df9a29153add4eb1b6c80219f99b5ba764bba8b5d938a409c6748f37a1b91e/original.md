```
test!(st::WSVarScoreTestInvariant, X1, W1)
```

Performs the score test, and returns the three p-values on the time-invariant test data.

# Arguments

  * `st::WSVarScoreTestInvariant`: data structure for the test
  * `X1::Union{Nothing, AbstractMatrix{T}}`: m x r*X1 data, nothing if r*X1 == 0
  * `W1::Union{Nothing, AbstractMatrix{T}}`: m x r*W1 data, nothing if r*W1 == 0
