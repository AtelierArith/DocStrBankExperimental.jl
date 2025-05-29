```
Lagrange(xs, [ws], coeffs, [var])
```

Lagrange interpolation of points `(xᵢ, fᵢ)` for `i ∈ 0..n`.

  * `xs`, `coeffs`: the interpolating coordinates.
  * `ws`: weights used in the barycentric representation. (From `SpecialPolynomials.lagrange_barycentric_weights` or `SpecialPolynomials.lagrange_barycentric_nodes_weights`.)
  * var: the polynomial indeterminate

# Extended help

The Lagrange interpolation of points `(xᵢ, fᵢ)` for `i ∈ 0:n` is the polynomial `p(x) = ∑ᵢ lⱼ(x) fⱼ`.

The basis vectors `lⱼ(x)` are `1` on `xⱼ` and `0` on `xᵢ` when `i ≠ j`. That is, `lⱼ(x) = Π_{i ≠ j}(x-xᵢ)/Π_{i ≠j}(xⱼ-xᵢ)`. These can be rewritten in terms of weights, `wⱼ`, depending on the `xᵢ` only, yielding `lⱼ = l(x) wⱼ/(x - xⱼ)` with `l(x) = Π(x-xᵢ)`. Going further, yields the barycentric formula:

`p(x) = (∑ wⱼ / (x - xⱼ) ⋅ fⱼ) /  (∑ wⱼ / (x - xⱼ) )`.

This representation has several properties, as detailed in Berrut and Trefethen [Barycentric Lagrange Interpolation](https://doi.org/10.1137/S0036144502417715).

## Examples

```jldoctest Lagrange
julia> using Polynomials, SpecialPolynomials

julia> p =  Lagrange([1,2,3], [1,2,3])
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> p.([1,2,3]) # the coefficients
3-element Vector{Int64}:
 1
 2
 3

julia> convert(Polynomial,  p)
Polynomial(1.0*x)
```

The instances hold the nodes and weights, which are necessary for representation, so the type alone can not be used for functions such as `variable` or `convert(Lagrange, ...)`. For the former we can use an instance, for the latter we can use `fit`:

```jldoctest Lagrange
julia> p =  Lagrange([1,2,3], [1,2,3])
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> variable(p)
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> q = Polynomial([0,0,1])
Polynomial(x^2)

julia> qq = fit(Lagrange, p.xs, p.ws, q)
Lagrange(1⋅ℓ_0(x) + 4⋅ℓ_1(x) + 9⋅ℓ_2(x))

julia> convert(Polynomial, qq)
Polynomial(1.0*x^2)
```

For a given set of nodes, `SpecialPolynomials.lagrange_barycentric_weights` can compute the weights.  For all but modest values of `n`, interpolating polynomials suffer from the Runge phenomenon unless the nodes are well chosen. (They should have asymptotic density of `1/√(1-x^2)` over `[-1,1]`.) For `P=Chebyshvev` and `P=ChebyshevU`, the function `SpecialPolynomials.lagrange_barycentric_nodes_weights(P, n)` will return a good choice of `n+1` points over `[-1,1]` along with precomputed weights.

```jldoctest Lagrange
julia> xs, ws = SpecialPolynomials.lagrange_barycentric_nodes_weights(SpecialPolynomials.ChebyshevBasis, 64);


julia> f(x) = exp(-x)*sinpi(x)
f (generic function with 1 method)

julia> p = fit(Lagrange, xs, f.(xs));


julia> degree(p)
64

julia> maximum(abs.(f(x) - p(x) for x in range(-1, 1, length=20))) <= 1e-14
true
```

!!! note
    The above example is more directly done through `fit(Chebyshev, f, 64)`, though the resulting polynomial will reference a different basis.

