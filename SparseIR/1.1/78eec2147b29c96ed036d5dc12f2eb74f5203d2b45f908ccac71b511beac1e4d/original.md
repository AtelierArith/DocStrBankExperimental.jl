```
FiniteTempBasis <: AbstractBasis
```

Intermediate representation (IR) basis for given temperature.

For a continuation kernel `K` from real frequencies, `ω ∈ [-ωmax, ωmax]`, to imaginary time, `τ ∈ [0, β]`, this type stores the truncated singular value expansion or IR basis:

```
K(τ, ω) ≈ sum(u[l](τ) * s[l] * v[l](ω) for l in 1:L)
```

This basis is inferred from a reduced form by appropriate scaling of the variables.

# Fields

  * `u::PiecewiseLegendrePolyVector`: Set of IR basis functions on the imaginary time (`tau`) axis. These functions are stored as piecewise Legendre polynomials.

    To obtain the value of all basis functions at a point or a array of points `x`, you can call the function `u(x)`. To obtain a single basis function, a slice or a subset `l`, you can use `u[l]`.
  * `uhat::PiecewiseLegendreFT`: Set of IR basis functions on the Matsubara frequency (`wn`) axis. These objects are stored as a set of Bessel functions.

    To obtain the value of all basis functions at a Matsubara frequency or a array of points `wn`, you can call the function `uhat(wn)`. Note that we expect reduced frequencies, which are simply even/odd numbers for bosonic/fermionic objects. To obtain a single basis function, a slice or a subset `l`, you can use `uhat[l]`.
  * `s`: Vector of singular values of the continuation kernel
  * `v::PiecewiseLegendrePoly`: Set of IR basis functions on the real frequency (`w`) axis. These functions are stored as piecewise Legendre polynomials.

    To obtain the value of all basis functions at a point or a array of points `w`, you can call the function `v(w)`. To obtain a single basis function, a slice or a subset `l`, you can use `v[l]`.
