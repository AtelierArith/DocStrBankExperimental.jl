```
unmarshal(T, dict[, verbose[, verboselvl]])
```

Reconstructs an object of Type T using the dictionary output of a `JSON.parse` or now 'LazyJSON.parse`.

Set verbose `true` to get debug information about how the data hierarchy is unmarshalled. This might be useful to track down parsing errors and/or mismatches between the JSON object and the Type definition.

# Example

```jldoctest
julia> using JSON

julia> var = randn(Float64, 5);  # Should work for most other variations of types you can think of

julia> unmarshal(typeof(var), JSON.parse(JSON.json(var)) ) == var
true
 
or 

julia> using LazyJSON

julia> var = randn(Float64, 5);  # Should work for most other variations of types you can think of

julia> unmarshal(typeof(var), LazyJSON.parse(JSON.json(var)) ) == var
true
```
