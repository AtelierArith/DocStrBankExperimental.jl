```
primitive_univariate_gcd!(p::_APL, q::_APL, algo::AbstractUnivariateGCDAlgorithm)
```

Returns the `gcd` of primitive polynomials `p` and `q` using algorithm `algo` which is a subtype of [`AbstractUnivariateGCDAlgorithm`](@ref). The function might modify `p` or `q`.
