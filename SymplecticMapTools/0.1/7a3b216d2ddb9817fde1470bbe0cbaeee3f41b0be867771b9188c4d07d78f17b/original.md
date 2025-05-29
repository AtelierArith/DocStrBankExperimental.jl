```
gn_circle(FJ::Function, z::InvariantCircle, Nθ::Integer;
          maxiter::Integer=10, rtol::Number=1e-8, verbose::Bool=false,
          monitor::Function=(z, rnorm) -> nothing,
          constraint::Function=fixed_θ0_constraint, λ::Number=0)
```

Find an invariant circle using Gauss-Newton with linesearch. Implemented with dense linear algebra (no FFTs yet). Returns the number of iterations taken to converge. If an evaluation fails, returns `-1`. If the routine fails to converge, returns `-2`

Arguments:

  * `z::InvariantCircle`: An initial connecting orbit guess, see `linear_initial_connecting_orbit`
  * `FJ::Function`: Function defined on R² with signature `F(x), J(x) = FJ(x)` where `F` is the symplectic map and `J = dF/dx`
  * `Nθ`: Number of quadrature nodes for the least squares
  * `maxiter = 10`: Maximum number of Gauss Newton steps
  * `rtol = 1e-8`: Stopping tolerance
