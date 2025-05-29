```julia
EnzymeVJP <: VJPChoice
```

Uses Enzyme.jl to compute vector-Jacobian products. Is the fastest VJP whenever applicable, though Enzyme.jl currently has low coverage over the Julia programming language, for example restricting the user's defined `f` function to not do things like require garbage collection or calls to BLAS/LAPACK. However, mutation is supported, meaning that in-place `f` with fully mutating non-allocating code will work with Enzyme (provided no high-level calls to C like BLAS/LAPACK are used) and this will be the most efficient adjoint implementation.

## Constructor

```julia
EnzymeVJP(; chunksize = 0)
```

## Keyword Arguments

  * `chunksize`: the default chunk size for the temporary variables inside the vjp's right hand side definition. This is used for compatibility with ODE solves that default to using ForwardDiff.jl for the Jacobian of the stiff ODE solve, such as OrdinaryDiffEq.jl. This should be set to the maximum chunksize that can occur during an integration to preallocate the `DualCaches` for PreallocationTools.jl. It defaults to 0, using `ForwardDiff.pickchunksize` but could be decreased if this value is known to be lower to conserve memory.
