```
convert_eltype(T, A)
```

Similar to `convert(T, A)`, but `T` refers to the eltype. See also [`_to_eltype`](@ref).

# Examples

```jldoctest; setup = :(using EltypeExtensions: convert_eltype)
julia> convert_eltype(Float64, 1:10)
1.0:1.0:10.0

julia> typeof(convert_eltype(Float64, rand(Int, 3, 3)))
Matrix{Float64} (alias for Array{Float64, 2})
```
