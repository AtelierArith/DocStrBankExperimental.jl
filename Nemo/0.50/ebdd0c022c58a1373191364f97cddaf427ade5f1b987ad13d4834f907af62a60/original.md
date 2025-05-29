```
is_unimodular(A::ZZMatrix)
is_unimodular(A::ZZMatrix; algorithm=:auto)
```

Determine whether a square matrix `A` is unimodular, i.e. whether `abs(det(A)) == 1`. The method used is either that of Pauderis–Storjohann or using CRT; the choice is made based on cost estimates for the two approaches.

The kwarg `algorithm` may be specified to be `:CRT` or `:pauderis_storjohann` to ensure that the corresponding underlying algorithm is used (after a quick initial unimodularity check).  `:CRT` is better if the matrix is unimodular and has an inverse containing large entries (or if it is not unimodular); `:pauderis_storjohann` is asymptotically faster when the matrix is unimodular and its inverse does not contain large entries, but it requires more space for intermediate expressions.
