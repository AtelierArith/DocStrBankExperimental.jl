```
struct FibonacciAnyon <: Sector
FibonacciAnyon(s::Symbol)
```

Represents the anyons of the Fibonacci modular fusion category. It can take two values, corresponding to the trivial sector `FibonacciAnyon(:I)` and the non-trivial sector `FibonacciAnyon(:τ)` with fusion rules $τ ⊗ τ = 1 ⊕ τ$.

## Fields

  * `isone::Bool`: indicates whether the sector corresponds the to trivial anyon `:I` (`true`), or the non-trivial anyon `:τ` (`false`).
