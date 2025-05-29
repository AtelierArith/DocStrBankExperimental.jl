```
galerkin_projection(
    f, B::AbstractBSplineBasis,
    [deriv = Derivative(0)], [VectorType = Vector{Float64}],
)
```

Perform Galerkin projection of a function `f` onto the given basis.

By default, returns a vector with values

$$
φ_i = ⟨ b_i, f ⟩
= ∫_a^b b_i(x) \, f(x) \, \mathrm{d}x,
$$

where $a$ and $b$ are the boundaries of the B-spline basis $\{ b_i \}_{i = 1}^N$.

The integrations are performed using Gauss–Legendre quadrature. The number of quadrature nodes is chosen so that the result is exact when $f$ is a polynomial of degree $k - 1$ (or, more generally, a spline belonging to the space spanned by the basis `B`). Here $k$ is the order of the B-spline basis. In the more general case, this function returns a quadrature approximation of the projection.

See also [`galerkin_projection!`](@ref) for the in-place operation, and [`galerkin_matrix`](@ref) for more details.
