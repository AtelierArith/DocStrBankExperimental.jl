```
StaticBitVector{N,C} = StaticElementVector{N,1,C}
StaticBitVector(x::AbstractVector)
```

## Examples

```jldoctest; setup=:(using ProblemReductions)
julia> sb = StaticBitVector([1,0,0,1,1])
10011

julia> sb[3]
0x0000000000000000

julia> collect(Int, sb)
5-element Vector{Int64}:
 1
 0
 0
 1
 1
```
