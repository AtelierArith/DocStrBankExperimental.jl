```
debye_function(n::Float64, β::Float64, x::Float64; 
              tol=1e-35, max_terms=2000) -> Float64
```

Compute the generalized Debye function with parameters `n`, `β`, and `x`.

References:

  * [Debye function](https://en.wikipedia.org/wiki/Debye_function)
  * [Paper](https://doi.org/10.1007/s10765-007-0256-1)
