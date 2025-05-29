```
encode(data::OrderedDict{String,Any})
```

`data`をLightBSONを使用してUInt8バッファにエンコードします。

# 例

```julia-repl
julia> data = OrderedDict(["test" => 10])
OrderedDict{String, Int64} with 1 entry:
  "test" => 10

julia> encode(data)
19-element Vector{UInt8}:
 0x13
 0x00
 0x00
 0x00
 0x12
    ⋮
 0x00
 0x00
 0x00
 0x00
 0x00
```
