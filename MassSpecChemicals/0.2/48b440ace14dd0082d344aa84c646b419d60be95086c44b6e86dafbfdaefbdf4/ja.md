```
Chemical <: AbstractChemical
```

名前、式、および追加の属性を持つ非構造化化学タイプ。

# フィールド

  * `name`: 一意の化学名（`String`）。
  * `formula`: 化学式（`String`）。
  * `attr`: 追加の属性（`Vector{Pair{Symbol, Any}}`）；ペアは属性名と値を表します。

# コンストラクタ

  * `Chemical(name::AbstractString, formula::AbstractString; kwargs_as_attr_pairs...)`
