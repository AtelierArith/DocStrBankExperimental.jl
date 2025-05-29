```
材料
```

材料とその特性を定義するために使用される構造体。

# 必須フィールド

  * `name::String` : 材料構造体の名前（または識別子）。
  * `density::Float64` : 密度 [g/cm³単位]。
  * `elements::Vector{String}` : 材料の組成に含まれる元素のベクター。
  * `weight_fractions::Vector{Float64}` : 材料の組成に含まれる各元素の重量分率のベクター。

# オプションフィールド - デフォルト値あり

  * `state_of_matter::String = "solid"` : 物質の状態。
