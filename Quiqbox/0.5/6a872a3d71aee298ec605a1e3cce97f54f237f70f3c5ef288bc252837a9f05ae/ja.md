```
GridBox{T, D, NP, GPT<:SpatialPoint{T, D}} <: SpatialStructure{T, D}
```

複数の `D` 次元グリッドポイントのコンテナです。

≡≡≡ フィールド ≡≡≡

`spacing::NTuple{D, T}`: 各次元に沿った隣接するグリッドポイント間の距離。

`nPoint::Int`: グリッドポイントの総数。

`point::NTuple{NP, GPT}`: [`SpatialPoint`](@ref) で表されるグリッドポイント。

`param::Tuple{Vararg{ParamBox{T}}}`: `GridBox` 内のすべてのパラメータ。

≡≡≡ 初期化メソッド ≡≡≡

```
GridBox(nGrids::NTuple{D, Int}, spacing::NTuple{D, Union{Array{T, 0}, T}}, 
        center::Union{AbstractVector{T}, NTuple{D, T}}=ntuple(_->T(0),Val(D)); 
        canDiff::NTuple{D, Bool}=ntuple(_->true, Val(D)), 
        index::NTuple{D, Int}=ntuple(_->0, Val(D))) where {T<:AbstractFloat, D} -> 
GridBox{T, D}

GridBox(nGrids::NTuple{D, Int}, spacingForAllDim::Union{T, Array{T, 0}}, 
        center::Union{AbstractVector{T}, NTuple{D, T}}=ntuple(_->T(0), Val(D)); 
        canDiff::Bool=true, index::Int=0) where {T<:AbstractFloat, D} -> 
GridBox{T, D}
```

一般的な `D` 次元の `GridBox` を構築します。

=== 位置引数 ===

`nGrids::NTuple{D, Int}`: 各次元に沿ったグリッドの数。

`spacing::NTuple{D, Union{Array{T, 0}, T}}`: 各次元に沿ったグリッドポイント間の間隔。

`spacingForAllDim::NTuple{D, Union{Array{T, 0}, T}}`: すべての次元に適用される単一の間隔。

`center::Union{AbstractVector{T}, NTuple{D, T}}`: グリッドボックスの幾何学的中心の座標。

=== キーワード引数 ===

`canDiff`::NTuple{D, Bool}: 構築された `GridBox` 内の各次元の `ParamBox` が微分可能としてマークされるかどうか。

`index`::NTuple{D, Int}: 保存された `ParamBox` の共有入力変数 `L` に割り当てられるインデックス。
