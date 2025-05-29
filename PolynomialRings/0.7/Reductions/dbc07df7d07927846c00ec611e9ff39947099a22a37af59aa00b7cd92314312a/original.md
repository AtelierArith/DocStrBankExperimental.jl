```
f_red = xrem(f, G)
```

Return the multivariate reduction of a polynomial `f` by a vector of polynomials `G`. By definition, this means that no leading term of a polynomial in `G` divides any monomial in `f`, and `f_red + factors * G == m * f` for some factors and for some integer `m`.

If you need to obtain the vector of factors, use `xdivrem` instead.

# Examples

In one variable, this is just the normal Euclidean algorithm:

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> xrem(x^2 + 1, [x-im])
0

julia> xrem(x^2 + y^2 + 1, [x, y])
1 + 0im
```
