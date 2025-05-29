```
MixedModelBootstrap{T<:AbstractFloat} <: MixedModelFitCollection{T}
```

`parametericbootstrap`によって返されるオブジェクトで、フィールドは次のとおりです。

  * `fits`: ブートストラップの複製からのパラメータ推定値を名前付きタプルのベクターとして格納します。
  * `λ`: `ReMat`モデル項からのλフィールドのコピーを含む`Vector{LowerTriangular{T,Matrix{T}}}`。
  * `inds`: `ReMat`モデル項からの`inds`フィールドのコピーを含む`Vector{Vector{Int}}`。
  * `lowerbd`: （[`OptSummary`](@ref)の同名フィールドに対応する）下限のベクターを含む`Vector{T}`。
  * `fcnames`: グルーピングファクター名をキーとし、列名を値とするNamedTuple。

`fits`のスキーマは、デフォルトで次のようになります。

```
Tables.Schema:
 :objective  T
 :σ          T
 :β          NamedTuple{β_names}{NTuple{p,T}}
 :se         StaticArrays.SArray{Tuple{p},T,1,p}
 :θ          StaticArrays.SArray{Tuple{k},T,1,k}
```

ここで、`β`および`θ`要素のサイズ`p`および`k`はモデルによって決定されます。

ブートストラップの複製の特性はプロパティとして抽出できます。`σs`および`σρs`プロパティは、`σ`および`θ`の推定値をランダム効果項の標準偏差と相関の推定値に展開します。
