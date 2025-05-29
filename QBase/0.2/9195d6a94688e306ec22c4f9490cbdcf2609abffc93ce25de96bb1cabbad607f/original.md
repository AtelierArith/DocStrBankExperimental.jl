```
pure_state( ψ :: Ket; atol=ATOL :: Float64 ) :: State
pure_state( ψ :: Bra; atol=ATOL :: Float64 ) :: State
```

A [`State`](@ref) is "pure" if it is rank-one (see [`is_pure`](@ref)). A rank-one density matrix is constructed by taking the outer-product of a [`Ket`](@ref) (or [`Bra`](@ref)) with itself, $|\psi\rangle\langle \psi| = \rho$. This method alternatively accepts `Vector` inputs.

```julia
pure_state( ψ :: Vector ) :: State
pure_state( ψ :: Adjoint{T,Vector{T}} where T; atol=ATOL :: Float64 ) :: State
```
