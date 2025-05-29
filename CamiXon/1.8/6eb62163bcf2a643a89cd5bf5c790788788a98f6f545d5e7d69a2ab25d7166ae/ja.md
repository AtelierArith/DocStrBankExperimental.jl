```
updatePos!(pos::Pos, E::T, Veff::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

エネルギー `E` から始めて、[`CamiDiff.Grid`](@extref) に表された有効ポテンシャルエネルギー（スクリーンされたクーロンポテンシャル） `Veff[n]` を用いて [`Pos`](@ref) オブジェクトを更新します。
