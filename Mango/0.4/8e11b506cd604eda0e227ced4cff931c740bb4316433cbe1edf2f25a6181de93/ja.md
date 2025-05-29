```
decode(buf::Vector{UInt8}, t::Type=OrderedDict{String, Any})
```

`buf`内のデータを`LightBSON.bson_read`を使用して型`t`のオブジェクトにデコードします。

# 例

```julia-repl
julia> data = OrderedDict(["test" => 10])
OrderedDict{String, Int64} with 1 entry:
  "test" => 10

julia> decode(encode(data))
OrderedDict{String, Any} with 1 entry:
  "test" => 10
```
