```
gn_connecting!(c::ConnectingOrbit, FJ::Function, ends::AbstractArray;
               Ns = 100, maxiters = 10, rtol = 1e-8, verbose=false)
```

Find a connecting orbit using Gauss Newton with linesearch.

Arguments:

  * `c::ConnectingOrbit`: An initial connecting orbit guess, see `linear_initial_connecting_orbit`
  * `FJ::Function`: Function defined on R² with signature  `F(x), J(x) = FJ(x)` where `F` is the symplectic map and `J = dF/dx`
  * `ends::AbstractArray`: A 2p × 2 matrix containing the end periodic orbits `[x00, x10; F(x00), F(x10); ... ; F^(p-1)(x00), F^(p-1)(x10)]`
  * `Ns = 100`: Number of quadrature nodes for the least squares
  * `maxiters = 10`: Maximum number of Gauss Newton steps
  * `rtol = 1e-8`: Stopping tolerance
