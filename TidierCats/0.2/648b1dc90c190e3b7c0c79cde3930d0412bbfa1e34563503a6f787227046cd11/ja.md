```
cat_lump_min(cat_array, min::Int, other_level::String = "Other")
```

カテゴリ配列の中で頻度が少ないレベルを最小カウントに基づいて「その他」レベルにまとめます。

# 引数

  * `cat_array`: まとめるカテゴリ配列
  * `min`: 最小カウントの閾値。この値未満のカウントのレベルはまとめられます。
  * `other_level`: 頻度が少ないレベルをまとめるためのレベル名。デフォルトは「Other」です。

# 戻り値

レベルがまとめられたカテゴリ配列。

# 例

```jldoctest  julia> cat_array = CategoricalArray(["A", "B", "B", "C", "C", "D"]) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"   "B"  "B"  "C"   "C"  "D"

julia> cat*lump*min(cat_array, 2)   6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"  "B"  "Other"  "Other"  "Other"  ```
