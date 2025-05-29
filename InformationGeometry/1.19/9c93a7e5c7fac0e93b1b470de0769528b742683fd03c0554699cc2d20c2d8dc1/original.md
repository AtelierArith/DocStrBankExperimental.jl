```
BiLog(x::Union{T, AbstractVector{T}}; C::Real=one(T)) where T<:Number
```

Computes bi-symmetric logarithm, which can also be applied to negative numbers

$$
BiLog(x) = \sgn(x) \sgn(C) \cdot \log(1 + |C| \cdot |x|)
$$

similar to the definition in https://doi.org/10.1088/0957-0233/24/2/027001 The constant `C` controls the slope of the bi-logarithm at zero. The inverse transformation is given by [`BiExp`](@ref).
