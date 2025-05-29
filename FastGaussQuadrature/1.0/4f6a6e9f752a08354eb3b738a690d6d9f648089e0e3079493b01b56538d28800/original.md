```
approx_besselroots(ν::Real, n::Integer) -> Vector{Float64}
```

Return the first $n$ roots of [Bessel function](https://en.wikipedia.org/wiki/Bessel_function). Note that this function is only 12-digits of precision.

$$
J_{\nu}(x) = \sum_{m=0}^{\infty}\frac{(-1)^j}{\Gamma(\nu+j+1)j!} \left(\frac{x}{2}\right)^{2j+\nu}
$$

# Examples

```jldoctest
julia> ν = 0.3;

julia> roots = approx_besselroots(ν, 10);

julia> zeros = (x -> besselj(ν, x)).(roots);

julia> all(zeros .< 1e-12)
true
```
