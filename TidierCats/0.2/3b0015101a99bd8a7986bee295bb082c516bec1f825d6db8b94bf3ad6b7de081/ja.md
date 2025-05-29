```
as_categorical(arr::AbstractArray)
```

入力配列をCategoricalArrayに変換します。

# 引数

`arr`: 入力配列。

# 戻り値

入力配列から構築されたCategoricalArray。

# 例

```jldoctest
julia> arr = ["A", "B", "C", "A", "B", "B", "D", "E", missing]
9-element Vector{Union{Missing, String}}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 missing
 
julia> as_categorical(arr)
9-element CategoricalArrays.CategoricalArray{Union{Missing, String},1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 missing
```
