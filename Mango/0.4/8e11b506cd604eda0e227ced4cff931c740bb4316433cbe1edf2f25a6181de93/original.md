```
decode(buf::Vector{UInt8}, t::Type=OrderedDict{String, Any})
```

Decode the data in `buf` into an object of type `t` using `LightBSON.bson_read`.

# Examples

```julia-repl
julia> data = OrderedDict(["test" => 10])
OrderedDict{String, Int64} with 1 entry:
  "test" => 10

julia> decode(encode(data))
OrderedDict{String, Any} with 1 entry:
  "test" => 10
```
