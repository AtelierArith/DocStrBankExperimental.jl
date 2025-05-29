cat*collapse(cat*array::CategoricalArray, levels_map::Dict)

提供されたマッピングに基づいて、カテゴリ変数の列のレベルを統合します。

# 引数

`cat_array`: 統合するカテゴリ変数の列。 levels_map: 元のレベルをキー、新しいレベルを値とする辞書。キーにないレベルはそのまま保持されます。

# 戻り値

レベルが統合されたカテゴリ配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "D", "E"], ordered=true)
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "D"
 "E"

julia> levels_map = Dict("A" => "A", "B" => "A", "C" => "C", "D" => "C", "E" => "E");

julia> cat_collapse(cat_array, levels_map)
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "A"
 "C"
 "C"
 "E"
```
