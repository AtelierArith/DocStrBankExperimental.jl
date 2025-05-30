```
cat_lump_prop(cat_array, prop::Float64, other_level::String = "Other")
```

カテゴリ配列の中で頻度の低いレベルを、割合の閾値に基づいて「その他」レベルにまとめます。

# 引数

  * `cat_array`: まとめるカテゴリ配列
  * `prop`: 割合の閾値。この値未満の割合を持つレベルがまとめられます。
  * `other_level`: 頻度の低いレベルをまとめるためのレベル名。デフォルトは「Other」です。

# 戻り値

割合に基づいてレベルがまとめられたカテゴリ配列。

# 例

```jldoctest julia> cat_array = CategoricalArray(["A", "B", "B", "C", "C", "D"]) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"   "B"  "C"  "C"   "D"

julia> cat*lump*prop(cat_array, 0.3) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"  "B"  "Other"   "Other"  "Other"  ```
