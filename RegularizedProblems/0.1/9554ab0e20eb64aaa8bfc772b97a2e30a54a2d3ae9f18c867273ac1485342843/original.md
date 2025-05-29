```
model, Av, selected = nnmf_model(m = 100, n = 50, k = 10, T = Float64)
```

Return an instance of an `NLPModel` representing the non-negative matrix factorization objective

```
f(W, H) = ½ ‖A - WH‖₂²,
```

where A ∈ Rᵐˣⁿ has non-negative entries and can be separeted into k clusters, `Av = A[:]`. The vector of indices `selected = k*m+1: k*(m+n)` is used to indicate the components of W ∈ Rᵐˣᵏ and H ∈ Rᵏˣⁿ to apply  the regularizer to (so that the regularizer only applies to entries of H).

## Arguments

  * `m :: Int`: the number of rows of A
  * `n :: Int`: the number of columns of A (with `n` ≥ `m`)
  * `k :: Int`: the number of clusters
