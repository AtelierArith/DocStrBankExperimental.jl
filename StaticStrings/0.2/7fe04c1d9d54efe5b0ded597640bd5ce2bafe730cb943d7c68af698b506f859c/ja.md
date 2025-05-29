```
StaticStrings.jl
```

StaticStrings.jl パッケージは `NTuple{N,UInt8}` に基づいた `AbstractString` を実装しています。

```jldoctest
julia> using StaticStrings

julia> static"Thank you for using StaticStrings.jl"
static"Thank you for using StaticStrings.jl"36

julia> static"Thank you for using StaticStrings.jl"64
static"Thank you for using StaticStrings.jl\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"64

julia> StaticString((0x48, 0x65, 0x6c, 0x6c, 0x6f, 0x20, 0x77, 0x6f, 0x72, 0x6c, 0x64))
static"Hello world"11
```

[`StaticString`](@ref), [`SubStaticString`](@ref), [`CStaticString`](@ref), [`PaddedStaticString`](@ref) を参照してください。
