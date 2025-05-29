```
map_keys(f, d)
```

Return a new document in which all keys are (recursively) transformed by callable `f`.

# Examples

```jldoctest
julia> d = Dict("a" => 1, "b" => Dict("c" => "foo"))
Dict{String, Any} with 2 entries:
  "b" => Dict("c"=>"foo")
  "a" => 1

julia> map_keys(Symbol, d)
Dict{Symbol, Any} with 2 entries:
  :a => 1
  :b => Dict(:c=>"foo")

julia> map_keys(string, d)
Dict{String, Any} with 2 entries:
  "b" => Dict("c"=>"foo")
  "a" => 1
```
