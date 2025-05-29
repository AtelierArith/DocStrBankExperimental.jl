```
BiExp(y::Union{T, AbstractVector{T}}; C::Real=one(T)) where T<:Number
```

Computes bi-symmetric exponential, which is the inverse transformation to [`BiLog`](@ref)

$$
BiExp(y) = \sgn(y) \cdot 1/C \cdot (\exp(|y|) - 1)
$$

similar to the definition in https://doi.org/10.1088/0957-0233/24/2/027001 The constant `C` controls the slope of the bi-logarithm at zero, i.e. the bi-exponential has slope `1/C`.
