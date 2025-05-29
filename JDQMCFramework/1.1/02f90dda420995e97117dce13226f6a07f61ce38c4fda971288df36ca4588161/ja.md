```
resize!(
    fgc::FermionGreensCalculator{T,E},
    G::Matrix{T}, logdetG::E, sgndetG::T,
    B::Vector{P}, n_stab::Int
) where {T<:Number, E<:AbstractFloat, P<:AbstractPropagator{T}}

resize!(
    fgc::FermionGreensCalculator{T,E}, n_stab::Int
) where {T,E}
```

新しい安定化周波数 `n_stab` を反映するように `fgc` を更新します。もし `G`、`logdetG`、`sgndetG` および `B` も渡されると、等時グリーン関数 `G` が再計算され、対応する更新された値 `(logdetG, sgndetG)` が返されます。
