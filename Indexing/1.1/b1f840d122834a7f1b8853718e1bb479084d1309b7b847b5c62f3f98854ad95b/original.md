```
ViewDict(parent, indices)
```

Create an array `out` which is a lazy view of `parent`. The indices of `out` match the indices of `indices`, and the values of `indices` are used to index `parent`. The parent must be an indexable type - for instance, an array or dictionary.

See also `ViewArray`, `view`.

# Examples

```julia
julia> d = Dict(:a => "Alice", :b => "Bob", :c => "Charlie")
Dict{Symbol,String} with 3 entries:
  :a => "Alice"
  :b => "Bob"
  :c => "Charlie"

julia> ViewDict(d, Dict(:aa => :a, :cc => :c))
ViewDict{Symbol,String,Dict{Symbol,String},Dict{Symbol,Symbol}} with 2 entries:
  :aa => "Alice"
  :cc => "Charlie"

julia> v = [11, 12, 13]
3-element Array{Int64,1}:
 11
 12
 13

julia> ViewDict(v, Dict(:a =>1 , :c => 3))
ViewDict{Symbol,Int64,Array{Int64,1},Dict{Symbol,Int64}} with 2 entries:
  :a => 11
  :c => 13
```
