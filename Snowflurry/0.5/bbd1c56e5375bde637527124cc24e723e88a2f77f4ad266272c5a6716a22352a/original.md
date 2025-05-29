```
read_response_body(body::Base.CodeUnits{UInt8,String})::String
```

Returns a `String` from Unicode code units.

See the [Julia documentation](https://docs.julialang.org/en/v1/base/strings/#lib-strings) for more details about code units.

# Example

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
