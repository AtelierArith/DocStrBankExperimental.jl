```
galerkin_matrix(
    [f::Function],
    B::AbstractBSplineBasis,
    [derivatives = (Derivative(0), Derivative(0))],
    [MatrixType = BandedMatrix{Float64}];
    [quadrature = default_quadrature((B, B))],
)
```

Compute Galerkin mass or stiffness matrix, as well as more general variants of these.

# Extended help

The Galerkin mass matrix is defined as

$$
M_{ij} = ⟨ ϕ_i, ϕ_j ⟩ \quad \text{for} \quad
i ∈ [1, N] \text{ and } j ∈ [1, N],
$$

where $ϕ_i(x)$ is the $i$-th basis function and `N = length(B)` is the number of functions in the basis `B`. Here, $⟨f, g⟩$ is the [$L^2$ inner product](https://en.wikipedia.org/wiki/Square-integrable_function#Properties) between functions $f$ and $g$.

Since products of B-splines are themselves piecewise polynomials, integrals can be computed exactly using [Gaussian quadrature rules](https://en.wikipedia.org/wiki/Gaussian_quadrature). To do this, we use Gauss–Legendre quadratures via the [FastGaussQuadrature](https://github.com/JuliaApproximation/FastGaussQuadrature.jl) package.

## Matrix layout and types

The mass matrix is banded with $2k - 1$ bands. Moreover, the matrix is symmetric and positive definite, and only $k$ bands are needed to fully describe the matrix. Hence, a [`Hermitian`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/index.html#LinearAlgebra.Hermitian) view of an underlying matrix is returned.

By default, the underlying matrix holding the data is a `BandedMatrix` that defines the upper part of the symmetric matrix. Other types of container are also supported, including regular sparse matrices (`SparseMatrixCSC`) and dense arrays (`Matrix`). See [`collocation_matrix`](@ref) for a discussion on matrix types.

!!! note "Periodic B-spline bases"
    The default matrix type is `BandedMatrix`, *except* for periodic bases ([`PeriodicBSplineBasis`](@ref)), in which case the Galerkin matrix has a few out-of-bands entries due to periodicity. For periodic bases, `SparseMatrixCSC` is the default. Note that this may change in the future.


## Derivatives of basis functions

Galerkin matrices associated to the derivatives of basis functions may be constructed using the optional `derivatives` parameter. For instance, if `derivatives = (Derivative(0), Derivative(2))`, the matrix $⟨ ϕ_i, ϕ_j'' ⟩$ is constructed, where primes denote derivatives. Note that, if the derivative orders are different, the resulting matrix is not symmetric, and a `Hermitian` view is not returned in those cases.

## Combining different bases

More generally, it is possible to compute matrices of the form $⟨ ψ_i^{(n)}, ϕ_j^{(m)} ⟩$, where `n` and `m` are derivative orders, and $ψ_i$ and $ϕ_j$ belong to two *different* (but related) bases `B₁` and `B₂`. For this, instead of the `B` parameter, one must pass a tuple of bases `(B₁, B₂)`. The restriction is that the bases must have the same parent B-spline basis. That is, they must share the same set of B-spline knots and be of equal polynomial order.

Note that, if both bases are different, the matrix will not be symmetric, and will not even be square if the bases have different lengths.

In practice, this feature may be used to combine a B-spline basis `B`, with a recombined basis `R` generated from `B` (see [Basis recombination](@ref basis-recombination-api)).

## Integrating more general functions

Say we wanted to integrate the more general term

$$
L_{ij} = ⟨ f(x) ϕ_i(x), ϕ_j(x) ⟩ = ∫_{a}^{b} f(x) ϕ_i(x) ϕ_j(x) \, \mathrm{d}x
$$

To obtain an approximation of this matrix, one would pass the $f(x)$ function as a first positional argument to `galerkin_matrix` (or [`galerkin_matrix!`](@ref)). This can also be combined with the `derivatives` argument if one wants to consider derivatives of $ϕ_i$ or $ϕ_j$.

Note that, in this case, the computation of the integrals is not guaranteed to be exact, since Gauss–Legendre quadratures are only "exact" when the integrand is a polynomial (the product of two B-splines is a piecewise polynomial). To improve accuracy, one may want to increase the number `n` of quadrature nodes. For this, pass `quadrature = Galerkin.gausslegendre(Val(n))` as a keyword argument.
