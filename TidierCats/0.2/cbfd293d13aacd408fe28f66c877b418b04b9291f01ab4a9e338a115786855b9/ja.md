```
cat_other(cat_array::CategoricalArray, other_level::String="Other")
```

すべてのレベルを「その他」レベルに置き換えます。

# 引数

  * `cat_array`: レベルを置き換えるためのカテゴリカル配列
  * `other_level`: すべてのレベルを置き換えるためのレベル名。デフォルトは「Other」です。

# 戻り値

すべてのレベルが「その他」レベルに置き換えられたカテゴリカル配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "D", "E"]);

julia> cat_other(cat_array, drop = ["A", "B"])
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "Other"
 "Other"
 "C"
 "D"
 "E"
```
