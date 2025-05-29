```
cat_rev(cat_array)
```

カテゴリカル配列のレベルの順序を逆にします。

# 引数

`cat_array`: 入力カテゴリカル配列。

# 戻り値

レベルの順序が逆になったカテゴリカル配列。

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

julia> cat_rev(cat_array)
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
```
