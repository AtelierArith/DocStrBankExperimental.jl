```
cat_infreq(cat_array)
```

カテゴリカル配列のレベルをその頻度によって並べ替え、最も一般的なレベルを最初にします。

# 引数

`cat_array`: 入力カテゴリカル配列。

# 戻り値

頻度によってレベルが再配置されたカテゴリカル配列。

# 例

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "B"], ordered=true)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "B"

julia> cat_infreq(cat_array)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "B"
```
