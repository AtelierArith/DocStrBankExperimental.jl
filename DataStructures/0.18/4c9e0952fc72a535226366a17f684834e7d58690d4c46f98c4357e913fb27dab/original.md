```
delete!(collection, key)
```

Delete the mapping for the given key in a collection, and return the collection.

# Examples

```jldoctest
julia> d = OrderedRobinDict("a"=>1, "b"=>2)
OrderedRobinDict{String, Int64} with 2 entries:
  "a" => 1
  "b" => 2

julia> delete!(d, "b")
OrderedRobinDict{String, Int64} with 1 entry:
  "a" => 1
```
