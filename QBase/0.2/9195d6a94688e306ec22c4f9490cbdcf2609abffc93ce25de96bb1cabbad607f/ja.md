```
pure_state( ψ :: Ket; atol=ATOL :: Float64 ) :: State
pure_state( ψ :: Bra; atol=ATOL :: Float64 ) :: State
```

[`State`](@ref) は「純粋」である場合、ランク1です（[`is_pure`](@ref]を参照）。ランク1の密度行列は、[`Ket`](@ref)（または[`Bra`](@ref)）の外積を取ることによって構築されます。$|\psi\rangle\langle \psi| = \rho$。このメソッドは、`Vector`入力も受け付けます。

```julia
pure_state( ψ :: Vector ) :: State
pure_state( ψ :: Adjoint{T,Vector{T}} where T; atol=ATOL :: Float64 ) :: State
```
