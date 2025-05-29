```
CollocationMatrix{T} <: AbstractBandedMatrix{T}
```

B-spline collocation matrix, defined by

$$
C_{ij} = b_j(x_i),
$$

where $\bm{x}$ is a set of collocation points.

Provides an efficient LU factorisation without pivoting adapted from de Boor (1978). The factorisation takes advantage of the total positivity of spline collocation matrices (de Boor 2001, p. 175).

# Factorisation

`CollocationMatrix` supports in-place LU factorisation using [`lu!`](@ref), as well as out-of-place factorisation using [`lu`](@ref). LU decomposition may also be performed via `factorize`.
