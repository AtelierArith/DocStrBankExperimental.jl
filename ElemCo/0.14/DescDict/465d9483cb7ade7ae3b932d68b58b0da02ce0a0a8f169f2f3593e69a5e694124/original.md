```
ODDict{K, V}
```

An ordered descriptive dictionary that maps keys of type `K` to values of type `V`.  Additionally, it stores a description of each key-value pair in the form of a string. 

The values are stored in an ordered dictionary, which means that the order of the key-value  pairs is preserved.

The values can be accessed using the `[]` syntax, e.g. `dict[key]`.  The descriptions can be accessed using the `()` syntax, e.g. `dict(key)`. The value and description can be set using the `[]` syntax, e.g. `dict[key] = value` or `dict[key] = (value, description)`, and the description can be set using the `()` syntax, e.g. `dict(key, description)`. New key-value pairs are always added to the end of the dictionary. If the key already exists in the dictionary, the value and description are updated. In order to add a key-value pair at the end of the dictionary, irrespectively  whether it is new or old, use the `push!` or `merge` functions.

### Examples

```julia
julia> dict = ODDict("a" => 1, "b" => 2)
ODDict{String, Int64}
  a => 1 ()
  b => 2 ()

julia> dict["a"]
1

julia> dict["c"] = 3
3

julia> push!(dict, "d" => 4)
ODDict{String, Int64}
  a => 1 ()
  b => 2 ()
  c => 3 ()
  d => 4 ()

julia> dict["a"] = (5, "this is a")
(5, "this is a")

julia> dict
ODDict{String, Int64}
  a => 5 (this is a)
  b => 2 ()
  c => 3 ()
  d => 4 ()

julia> push!(dict, "a" => (5,"this is a"), "e" => (6,"this is e"))
ODDict{String, Int64}
  b => 2 ()
  c => 3 ()
  d => 4 ()
  a => 5 (this is a)
  e => 6 (this is e)
```
