```
BiPower(y::Union{T, AbstractVector{T}}, m::Real=2.0; C::Real=one(T)) where T<:Number
```

Computes bi-symmetric `m`-th power, which is the inverse transformation to [`BiRoot`](@ref) in such a way that the slope of [`BiPower`](@ref) is `1/C` at the origin (i.e. the slope of the original [`BiRoot`](@ref) is `C`):

$$
BiPower_m(y) = \sgn(x) \cdot (m C)^{-1} \cdot ((1 + |y|)^m - 1)
$$

The bi-symmetric root and power are inspired by the bi-symmetric logarithm in https://doi.org/10.1088/0957-0233/24/2/027001
