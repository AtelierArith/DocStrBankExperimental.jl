```
findranges(f, A::AbstractArray)
```

Find each range on `eachindex(A)` over which `isequal(f(A[i]), f(A[i+δ]))` is true, with the first range starting at `i=firstindex(A)`; subsequent ranges start from `i=i+δⱼ+1` where `δⱼ` is the difference between the stop and start of the previous range.

# Examples

```jldoctest
julia> findranges(signbit, -5:5)
2-element Vector{UnitRange{Int64}}:
 1:5
 6:11

julia> findranges(identity, [0, missing, missing, 1, 1])
3-element Vector{UnitRange{Int64}}:
 1:1
 2:3
 4:5
```
