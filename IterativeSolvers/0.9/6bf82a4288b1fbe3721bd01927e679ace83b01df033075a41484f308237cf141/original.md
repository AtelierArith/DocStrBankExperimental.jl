```
powm!(B, x; shift = zero(eltype(B)), inverse::Bool = false, kwargs...) -> λ, x, [history]
```

By default finds the approximate eigenpair `(λ, x)` of `B` where `|λ|` is largest.

# Arguments

  * `B`: linear map, see the note below.
  * `x`: normalized initial guess. Don't forget to use complex arithmetic when necessary.

## Keywords

  * `tol::Real = eps(real(eltype(B))) * size(B, 2) ^ 3`: stopping tolerance for the residual norm;
  * `maxiter::Integer = size(B,2)`: maximum number of iterations;
  * `log::Bool`: keep track of the residual norm in each iteration;
  * `verbose::Bool`: print convergence information during the iterations.

!!! note "Shift-and-invert"
    When applying shift-and-invert to $Ax = λx$ with `invert = true` and `shift = ...`, note that the role of `B * b` becomes computing `inv(A - shift I) * b`. So rather than passing the linear map $A$ itself, pass a linear map `B` that has the action of shift-and-invert. The eigenvalue is transformed back to an eigenvalue of the actual matrix $A$.


# Return values

**if `log` is `false`**

  * `λ::Number` approximate eigenvalue computed as the Rayleigh quotient;
  * `x::Vector` approximate eigenvector.

**if `log` is `true`**

  * `λ::Number`: approximate eigenvalue computed as the Rayleigh quotient;
  * `x::Vector`: approximate eigenvector;
  * `history`: convergence history.

**ConvergenceHistory keys**

  * `:tol` => `::Real`: stopping tolerance;
  * `:resnom` => `::Vector`: residual norm at each iteration.

# Examples

```julia
using LinearMaps
σ = 1.0 + 1.3im
A = rand(ComplexF64, 50, 50)
F = lu(A - σ * I)
Fmap = LinearMap{ComplexF64}((y, x) -> ldiv!(y, F, x), 50, ismutating = true)
λ, x = powm(Fmap, inverse = true, shift = σ, tol = 1e-4, maxiter = 200)
```
