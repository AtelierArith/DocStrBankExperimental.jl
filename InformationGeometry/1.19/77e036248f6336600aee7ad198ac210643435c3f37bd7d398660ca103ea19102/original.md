```
BiRoot(x::Union{T, AbstractVector{T}}, m::Real=2.0; C::Real=one(T)) where T<:Number
```

Computes bi-symmetric `m`-th root, which is the inverse transformation to [`BiPower`](@ref) in such a way that the slope is `C` at the origin:

$$
BiRoot_m(x) = \sgn(x) \sgn(C) \cdot ((1 + m \cdot |C| \cdot |x|)^{1/m} -1)
$$

The bi-symmetric root and power are inspired by the bi-symmetric logarithm in https://doi.org/10.1088/0957-0233/24/2/027001
