```
valuelabels(x::AbstractArray{<:LabeledValue})
```

`x`のすべての要素の値ラベルを返すイテレータを返します。返されるオブジェクトは、`x`と同じサイズの`AbstractArray`のサブタイプです。

このイテレータは、基になる値を破棄しながら、値ラベルを配列に収集するために使用できます。

# 例

```jldoctest
julia> x = LabeledArray([1, 2, 3], Dict(1=>"a", 2=>"b"))
3-element LabeledVector{Int64, Vector{Int64}, Int64}:
 1 => a
 2 => b
 3 => 3

julia> lbls = valuelabels(x)
3-element ReadStatTables.LabelIterator{LabeledVector{Int64, Vector{Int64}, Int64}, 1}:
 "a"
 "b"
 "3"

julia> collect(lbls)
3-element Vector{String}:
 "a"
 "b"
 "3"

julia> CategoricalArray(lbls)
3-element CategoricalArray{String,1,UInt32}:
 "a"
 "b"
 "3"
```
