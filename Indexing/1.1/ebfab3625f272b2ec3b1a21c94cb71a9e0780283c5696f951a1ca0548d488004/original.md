```
ViewArray(parent, indices)
```

Create an array `out` which is a lazy view of `parent`. The indices of `out` match the indices of `indices`, and the values of `indices` are used to index `parent`. Unlike `SubArray`, the parent type could be any indexable container (for instance, we can create an `AbstractArray` view of the values stored in an `AbstractDict`).

See also `ViewDict`, `view`.

# Examples

```julia
julia> d = Dict(:a => 11, :b => 12, :c => 13)
Dict{Symbol,Int64} with 3 entries:
  :a => 11
  :b => 12
  :c => 13

julia> ViewArray(d, [:a, :c])
2-element ViewArray{Int64,1,Dict{Symbol,Int64},Array{Symbol,1}}:
 11
 13
```
