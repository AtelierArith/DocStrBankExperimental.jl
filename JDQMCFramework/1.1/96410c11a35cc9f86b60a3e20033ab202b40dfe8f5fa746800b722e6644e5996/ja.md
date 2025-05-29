```
FermionGreensCalculator(
    B::AbstractVector{P},
    β::E, Δτ::E, n_stab::Int
) where {T<:Number, E<:AbstractFloat, P<:AbstractPropagator{T}}
```

渡された伝播子のベクトル `B` に基づいて [`FermionGreensCalculator`](@ref) 構造体を初期化して返します。
