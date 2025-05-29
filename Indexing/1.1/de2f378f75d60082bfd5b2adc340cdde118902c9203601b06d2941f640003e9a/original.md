getindices(container, indices)

Return an indexable container with indices `keys(indices)` and values `container[i]` for `i ∈ values(indices)`. This generalizes scalar `getindex(container, index)` for multiple indices, for dictionaries, tuples, named tuples, etc.

# Examples

```julia
julia> d = Dict(:a => "Alice", :b => "Bob", :c => "Charlie")
Dict{Symbol,String} with 3 entries:
  :a => "Alice"
  :b => "Bob"
  :c => "Charlie"

julia> getindices(d, [:a, :c])
2-element Array{String,1}:
 "Alice"  
 "Charlie"

julia> getindices(d, (:a, :c))
("Alice", "Charlie")

julia> getindices(d, Dict("Wife" => :a, "Husband" => :c))
Dict{String,String} with 2 entries:
  "Wife"    => "Alice"
  "Husband" => "Charlie"
```
