```
padded"string[PAD]"N
```

Create a [`PaddedStaticString`](@ref) of `N` codeunits from "string". The last codeunit in the provided string becomes the `PAD`.

# Examples

```jldoctest
julia> padded"私は元気です。 ありがとうございました。 "64
padded"私は元気です。 ありがとうございました。 "64

julia> padded"私は元気です。 ありがとうございました。 "64 |> StaticString
static"私は元気です。 ありがとうございました。      "64
```
