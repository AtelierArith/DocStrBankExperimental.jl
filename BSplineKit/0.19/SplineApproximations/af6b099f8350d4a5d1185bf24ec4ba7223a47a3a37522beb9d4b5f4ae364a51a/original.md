```
MinimiseL2Error <: AbstractApproxMethod
```

Approximate a given function $f(x)$ by minimisation of the $L^2$ distance between $f$ and its spline approximation $g(x)$.

# Extended help

Minimises the $L^2$ distance between the two functions:

$$
{\left\lVert f - g \right\rVert}^2 = \left< f - g, f - g \right>,
$$

where

$$
\left< u, v \right> = ∫_a^b u(x) \, v(x) \, \mathrm{d}x
$$

is the inner product between two functions, and $a$ and $b$ are the boundaries of the prescribed B-spline basis. Here, $g$ is the spline $g(x) = ∑_{i = 1}^N c_i \, b_i(x)$, and $\{ b_i \}_{i = 1}^N$ is a prescribed B-spline basis.

One can show that the optimal coefficients $c_i$ minimising the $L^2$ error are the solution to the linear system $\bm{M} \bm{c} = \bm{φ}$, where $M_{ij} = \left< b_i, b_j \right>$ and $φ_i = \left< b_i, f \right>$. These two terms are respectively computed by [`galerkin_matrix`](@ref) and [`galerkin_projection`](@ref).

The integrals associated to $\bm{M}$ and $\bm{φ}$ are computed via Gauss–Legendre quadrature. The number of quadrature nodes is chosen as a function of the order $k$ of the prescribed B-spline basis, ensuring that $\bm{M}$ is computed exactly (see also [`galerkin_matrix`](@ref)). In the particular case where $f$ is a polynomial of degree $k - 1$, this also results in an exact computation of $\bm{φ}$. In more general cases, as long as $f$ is smooth enough, this is still expected to yield a very good approximation of the integral, and thus of the optimal coefficients $c_i$.
