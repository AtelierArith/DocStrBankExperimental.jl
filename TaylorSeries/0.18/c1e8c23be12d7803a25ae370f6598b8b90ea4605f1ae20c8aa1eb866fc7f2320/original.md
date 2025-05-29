```
TaylorN([T::Type=Float64], nv::Int; [order::Int=get_order()])
```

Shortcut to define the `nv`-th independent `TaylorN{T}` variable as a polynomial. The order is defined through the keyword parameter `order`, whose default corresponds to `get_order()`. The default of type for `T` is `Float64`.

```julia
julia> TaylorN(1)
 1.0 x₁ + 𝒪(‖x‖⁷)

julia> TaylorN(Rational{Int},2)
 1//1 x₂ + 𝒪(‖x‖⁷)
```
