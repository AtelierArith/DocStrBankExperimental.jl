```
Taylor1([T::Type=Float64], order::Int)
```

Shortcut to define the independent variable of a `Taylor1{T}` polynomial of given `order`. The default type for `T` is `Float64`.

```julia
julia> Taylor1(16)
 1.0 t + 𝒪(t¹⁷)

julia> Taylor1(Rational{Int}, 4)
 1//1 t + 𝒪(t⁵)
```
