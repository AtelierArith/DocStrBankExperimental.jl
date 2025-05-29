```
factors = div!(f, G)
```

Compute the multivariate reduction of a polynomial `f` by a vector of polynomials `G`, in-place. By definition, this means that after applying `rem!` no, leading term of a polynomial in `G` divides any monomial in `f`, and `f + factors * G` is equal to the original value of `f`.

The return value is `nothing` if no reduction has taken place. This situation could also be represented by the zero vector, but we choose `nothing` for efficiency.

If you want to allow clearing denominators, e.g. reduce `2x^2` by `3x` even though your base ring is ℤ, use `xdiv!` instead.

# Examples

In one variable, this is just the normal Euclidean algorithm:

```jldoctest
julia> using PolynomialRings

julia> R,(x,y) = polynomial_ring(:x, :y, basering=Complex{Int});

julia> f = x^2 + 1 + 0im
x^2 + 1 + 0im

julia> collect(div!(f, [x-im]))
1×1 Array{@ring(Complex{Int64}[x,y]),2}:
 x + 0 + 1im

julia> f
0

julia> g = x^2 + y^2 + 1
x^2 + y^2 + 1 + 0im

julia> collect(div!(g, [x, y]))
1×2 Array{@ring(Complex{Int64}[x,y]),2}:
 x  y

julia> g
1 + 0im
```
