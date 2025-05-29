```
MixedModelPermutation{T<:AbstractFloat}
```

さまざまな置換メソッドによって返されるオブジェクトで、フィールドは次のとおりです。

  * `fits`: 名前付きタプルのベクトルとしての置換複製からのパラメータ推定値。
  * `λ`: `Vector{LowerTriangular{T,Matrix{T}}}` で、`ReMat` モデル項からの `λ` フィールドのコピーを含む。
  * `inds`: `Vector{Vector{Int}}` で、`ReMat` モデル項からの `inds` フィールドのコピーを含む。
  * `lowerbd`: `Vector{T}` で、下限のベクトルを含む（[`OptSummary`](@ref) の同名フィールドに対応）。
  * `fcnames`: グループ化因子名をキーとし、列名を値とする NamedTuple。

`fits` のスキーマは、デフォルトで次のようになります。

```
Tables.Schema:
 :objective  T
 :σ          T
 :β          NamedTuple{β_names}{NTuple{p,T}}
 :se         StaticArrays.SArray{Tuple{p},T,1,p}
 :θ          StaticArrays.SArray{Tuple{k},T,1,k}
```

ここで、`β` および `θ` 要素のサイズ `p` と `k` はモデルによって決定されます。

置換複製の特性はプロパティとして抽出できます。 `σs` および `σρs` プロパティは、`σ` および `θ` の推定値をランダム効果項の標準偏差と相関の推定値に展開します。
