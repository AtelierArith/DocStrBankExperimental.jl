```
hermiteH(n::Integer, x::T [; deriv=0 [, msg=true]]) where T<:Real
```

Hermite polynomal of degree `n`,

$$
    H_{n}(x)
    = (-1)^ne^{x^2}\frac{d^{n}}{dx^{n}}(e^{-x^2})
    = \sum_{k=0}^{n}(-1)^{m}\frac{n!}{k!}\frac{(2x)^{k}}{m!}
    = \sum_{k=0}^{n}c_k(n)x^{k}
$$

where $m = (n-k)/2$ and the $c_k(n)$ are hermite coefficients of [`hermite_polynom`](@ref).

#### Example:

```
julia> hermite_polynom(7)
(0, -1680, 0, 3360, 0, -1344, 0, 128)

julia>  polynom = hermite_polynom(8)
(1680, 0, -13440, 0, 13440, 0, -3584, 0, 256)

julia> polynomial(polynom, 5)
52065680

julia> hermiteH(8, 5)
52065680
```
