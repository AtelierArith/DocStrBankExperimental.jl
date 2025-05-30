```
read_response_body(body::Base.CodeUnits{UInt8,String})::String
```

Unicode コードユニットから `String` を返します。

コードユニットの詳細については、[Julia ドキュメント](https://docs.julialang.org/en/v1/base/strings/#lib-strings)を参照してください。

# 例

```jldoctest
julia> string = "my string"
"my string"

julia> body = codeunits(string)
9-element Base.CodeUnits{UInt8, String}:
 0x6d
 0x79
 0x20
 0x73
 0x74
 0x72
 0x69
 0x6e
 0x67

julia> read_response_body(body)
"my string"

```
