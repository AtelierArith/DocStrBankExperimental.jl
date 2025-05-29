```
SymbolicsSparsityDetection(; alg = GreedyD1Color())
```

Use Symbolics to compute the sparsity pattern of the Jacobian. This requires `Symbolics.jl` to be explicitly loaded.

## Keyword Arguments

```
- `alg`: The algorithm used for computing the matrix colors
```

See Also: [JacPrototypeSparsityDetection](@ref), [PrecomputedJacobianColorvec](@ref)
