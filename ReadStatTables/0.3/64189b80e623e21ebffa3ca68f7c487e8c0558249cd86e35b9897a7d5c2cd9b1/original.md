```
valuelabels(x::AbstractArray{<:LabeledValue})
```

Return an iterator over the value labels of all elements in `x`. The returned object is a subtype of `AbstractArray` with the same size of `x`.

The iterator can be used to collect value labels to arrays while discarding the underlying values.

# Examples

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
