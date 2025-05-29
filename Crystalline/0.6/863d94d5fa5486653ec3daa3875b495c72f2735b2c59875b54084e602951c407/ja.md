```
SymmetryVector{D} <: AbstractSymmetryVector{D}
```

次元 `D` の対称ベクトルで、特徴的な不変表現（irreps）とその重複度、全体のバンド占有数を含みます。

## フィールド

  * `lgirsv :: Vector{Collection{LGIrrep{D}}}` (`const`): 空間群の各高対称 **k**-点に関連付けられた `LGIrrep{D}` コレクションのベクトル。
  * `multsv :: Vector{Vector{Int}}` (`const`): 関連する不変表現の重複度のベクトル。対称ベクトルにおいて不変表現 `lgirsv[i][j]` は重複度 `multsv[i][j]` で出現します。
  * `occupation :: Int`: 対称ベクトルに関連する占有（バンド数）。

## インターフェース

  * `SymmetryVector` の不変表現、重複度、バンド占有はそれぞれ `irreps`、`multiplicities`、`occupation` を介して取得できます。
  * `SymmetryVector` の不変表現ラベル、**k**-ラベル、空間群番号はそれぞれ `irreplabels`、`klabels`、`num` を介して利用可能です。
  * `SymmetryVector` は `Vector` を介して「生」の連結ベクトル表現に変換できます。

## 構築

  * 文字列から: `parse(::Type{SymmetryVector{D}}, ::AbstractString, ::Vector{Collection{LGIrrep{D}}})` を参照してください。
  * 「生」の連結ベクトルから: [`SymmetryVector`](@ref)`(::AbstractVector{<:Integer}, ...)` を参照してください。
