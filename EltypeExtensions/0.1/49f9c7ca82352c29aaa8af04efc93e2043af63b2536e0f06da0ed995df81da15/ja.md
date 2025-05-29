```
convert_eltype(T, A)
```

`convert(T, A)`と似ていますが、`T`はeltypeを指します。詳細は[`_to_eltype`](@ref)を参照してください。

# 例

```jldoctest; setup = :(using EltypeExtensions: convert_eltype)
julia> convert_eltype(Float64, 1:10)
1.0:1.0:10.0

julia> typeof(convert_eltype(Float64, rand(Int, 3, 3)))
Matrix{Float64} (alias for Array{Float64, 2})
```
