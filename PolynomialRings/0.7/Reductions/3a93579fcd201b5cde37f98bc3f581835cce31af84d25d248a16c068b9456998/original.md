```
m, factors = xdiv!(f, G)
```

Compute the multivariate reduction of a polynomial `f` by a vector of polynomials `G`, in-place. By definition, this means that after applying `rem!` no, leading term of a polynomial in `G` divides any monomial in `f`, and `f + factors * G` is equal to `m` times the original value of `f`.

The difference between `xdiv!` and `div` is that the former allows clearing denominators, e.g. reduce `2x^2` by `3x` even when the base ring is ℤ.

# Examples

In one variable, this is just the normal Euclidean algorithm:

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> xdiv!(f, [x-im])
(1 + 0im, @ring(Complex{Int64}[x,y])[x + 0 + 1im])

julia> f
y^2

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> xdiv!(g, [x, y])
(1 + 0im, @ring(Complex{Int64}[x,y])[x y])

julia> g
1 + 0im
```
