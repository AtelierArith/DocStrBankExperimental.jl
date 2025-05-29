```
delete!(collection, key)
```

Delete the mapping for the given key in a collection, and return the collection.

# Examples

```jldoctest
julia> d = RobinDict("a"=>1, "b"=>2)
RobinDict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
RobinDict{String, Int64} with 1 entry:
  "a" => 1
```
