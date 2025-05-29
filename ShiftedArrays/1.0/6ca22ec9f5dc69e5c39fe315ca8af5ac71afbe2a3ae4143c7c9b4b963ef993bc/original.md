```
lead(v::AbstractArray, n = 1; default = missing)
```

Return a `ShiftedArray` object, with underlying data `v`. The second argument gives the amount to shift negatively in each dimension. If it is an integer, it is assumed to refer to the first dimension. `default` specifies a default value when you are out of bounds.

# Examples

```jldoctest lead
julia> v = [1, 3, 5, 4];

julia> lead(v)
4-element ShiftedArray{Int64,Missing,1,Array{Int64,1}}:
 3
 5
 4
  missing

julia> w = 1:2:9
1:2:9

julia> s = lead(w, 2)
5-element ShiftedArray{Int64,Missing,1,StepRange{Int64,Int64}}:
 5
 7
 9
  missing
  missing

julia> copy(s)
5-element Array{Union{Missing, Int64},1}:
 5
 7
 9
  missing
  missing

julia> v = reshape(1:16, 4, 4);

julia> s = lead(v, (0, 2))
4×4 ShiftedArray{Int64,Missing,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}}}:
  9  13  missing  missing
 10  14  missing  missing
 11  15  missing  missing
 12  16  missing  missing
```
