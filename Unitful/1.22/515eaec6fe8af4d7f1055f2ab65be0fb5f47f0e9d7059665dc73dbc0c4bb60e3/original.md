```
ustrip(u::Units, x::Quantity)
ustrip(T::Type, u::Units, x::Quantity)
```

Convert `x` to units `u` using [`uconvert`](@ref) and return the number out the front of the resulting quantity. If `T` is supplied, also `convert` the resulting number into type `T`.

This function is mainly intended for compatibility with packages that don't know how to handle quantities.

```jldoctest
julia> ustrip(u"m", 1u"mm") == 1//1000
true

julia> ustrip(Float64, u"m", 2u"mm") == 0.002
true
```

`ustrip` supports `InverseFunctions.inverse`:

```jldoctest
julia> using InverseFunctions: inverse

julia> inverse(Base.Fix1(ustrip, u"m"))(5)
5 m
```
