```
exp!(
    exppαH::AbstractMatrix{T},
    expmαH::AbstractMatrix{T},
    H::AbstractMatrix{T}, α::E;
    # KEYWORD ARGUMENTS
    workspace::HermitianEigenWs{T,Matrix{T},R} = HermitianEigenWs(H),
    tol::R = 1e-6
) where {T<:Number, E<:Number, R<:AbstractFloat}
```

Given a Hermitian matrix `H`, calculate the matrix exponentials $e^{+\alpha H}$ and $e^{-\alpha H}$, which are written to `exppαH` and `expmαH` respectively. Note that `H` is left modified by this method. The `workspace` field is of type [`HermitianEigenWs`](https://dynarejulia.github.io/FastLapackInterface.jl/dev/workspaces/#FastLapackInterface.HermitianEigenWs), which is exported from the [`FastLapackInterface.jl`](https://github.com/DynareJulia/FastLapackInterface.jl) package, is used to avoid dynamic memory allocations.
