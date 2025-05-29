```
precisiontype(T::Type)
```

Returns the type that decides the precision of `T`. The difference from [`basetype`](@ref) is that `precisiontype` unwraps composite basetypes such as `Complex` and that `precisiontype` is not generalised.

# Examples

```jldoctest; setup = :(using EltypeExtensions: precisiontype)
julia> precisiontype(Complex{Float32})
Float32

julia> precisiontype(Matrix{ComplexF64})
Float64
```
