```
cat_relevel(cat_array::CategoricalArray, levels_order::Vector{String}, after::Int=0)
```

提供された順序に従って、カテゴリカル配列のレベルを再配置します。

# 引数

`cat_array`: 入力カテゴリカル配列。 `levels_order`: 希望する順序のレベルのベクター。 `after`: 新しいレベルを挿入する位置。デフォルトは無視されます。

# 戻り値

levels_orderに従ってレベルが再配置されたカテゴリカル配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", "B"], ordered=true)
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"

julia> println(levels(cat_relevel(cat_array, ["B", "A", "C"])))
["B", "A", "C"]

julia> println(levels(cat_relevel(cat_array, ["A"], after=1)))
["B", "A", "C"]

julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", missing], ordered=true);

julia> println(levels(cat_relevel(cat_array, ["C", "A", "B", missing]), skipmissing=false))
Union{Missing, String}["C", "A", "B", missing]
```
