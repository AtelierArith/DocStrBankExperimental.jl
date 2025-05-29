```
castPos(E::T, Veff::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

エネルギー `E` と [`CamiDiff.Grid`](@extref) にタブ化された有効ポテンシャルエネルギー（スクリーンされたクーロンポテンシャル） `Veff[n]` から [`Pos`](@ref) オブジェクトを作成します。
