```
cat_replace_missing(cat_array::CategoricalArray, missing_level::String = "missing")
```

欠損値をプレースホルダー文字列である "missing" で置き換えます。

# 引数

  * `cat_array`: まとめるためのカテゴリカル配列
  * `missing_level`: 欠損値の代わりに使用される文字列。

# 戻り値

欠損要素のないカテゴリカル配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["apple", "tomato", missing, "dear"])
4-element CategoricalArrays.CategoricalArray{Union{Missing, String},1,UInt32}:
 "apple"
 "tomato"
 missing
 "dear"

julia> cat_replace_missing(cat_array)
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "apple"
 "tomato"
 "missing"
 "dear"

julia> cat_replace_missing(cat_array, "unknown")
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "apple"
 "tomato"
 "unknown"
 "dear"
```
