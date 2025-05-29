```
SparsePattern(::FD, func!, ng, x1, x2, x3)
```

detect sparsity pattern by computing derivatives (using finite differencing) at three different locations. Entries that are zero at all three  spots are assumed to always be zero.

# Arguments

  * `func!::Function`: function of form f = func!(g, x)
  * `ng::Int`: number of constraints
  * `x1,x2,x3::Vector{Float}`:: three input vectors.
