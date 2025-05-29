```
laguerreL(n::Integer, x::T [; deriv=0 [, msg=true]]) where T<:Real
```

Laguerre polynomal of degree `n`,

$$
    L_{n}(x)
    = \frac{1}{n!}e^{x}\frac{d^{n}}{dx^{n}}(e^{-x}x^{n})
    = \sum_{k=0}^{n}(-1)^{k}\binom{n}{n-k}\frac{x^{k}}{k!}
    = \sum_{k=0}^{n}c_k(n)x^{k}
$$

where the $c_k(n)$ are Laguerre coefficients of [`laguerre_polynom`](@ref).

#### Example:

```
julia> polynom = laguerre_polynom(8); println(polynom)
(1//1, -8//1, 14//1, -28//3, 35//12, -7//15, 7//180, -1//630, 1//40320)

julia> polynomial(polynom, 5)
18029//8064

julia> laguerreL(8, 5)
18029//8064

julia> (xmin, Δx, xmax) = (0, 0.1, 11);
julia> n = 8;
julia> L = [laguerreL(n, x) for x=xmin:Δx:xmax];
julia> f = Float64.(L);
plot_function(f, xmin, Δx, xmax; title="laguerre polynomial (of degree $n)")
```

The plot is made using `CairomMakie`. NB.: `plot_function` is not included in the `CamiXon` package. ![Image](../assets/laguerreL8.png)
