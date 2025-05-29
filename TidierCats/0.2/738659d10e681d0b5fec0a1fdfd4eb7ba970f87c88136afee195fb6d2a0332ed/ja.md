```
cat_lump(cat_array, n::Int)
```

カテゴリカル配列のレベルをその頻度によって並べ替え、最も一般的な 'n' レベルのみを保持します。他のすべてのレベルは「Other」に置き換えられます。

引数 `cat_array`: 入力カテゴリカル配列。 `n`: そのまま保持するレベルの数、残りは「Other」になります。

# 戻り値

最も頻度の低いレベルが「Other」としてまとめられたカテゴリカル配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", "B", "D", "E", "F"], ordered=true)
9-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 "F"
```
