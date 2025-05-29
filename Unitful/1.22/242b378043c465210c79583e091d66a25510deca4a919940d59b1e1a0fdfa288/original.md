```
uconvert(a::Units, x::Quantity{T,D,U}) where {T,D,U}
```

Convert a [`Unitful.Quantity`](@ref) to different units. The conversion will fail if the target units `a` have a different dimension than the dimension of the quantity `x`. You can use this method to switch between equivalent representations of the same unit, like `N m` and `J`.

Example:

```jldoctest
julia> uconvert(u"hr",3602u"s")
1801//1800 hr

julia> uconvert(u"J",1.0u"N*m")
1.0 J
```
