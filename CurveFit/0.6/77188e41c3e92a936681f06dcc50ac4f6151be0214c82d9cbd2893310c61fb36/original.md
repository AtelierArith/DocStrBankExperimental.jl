a = gauss*newton*fit(x, y, fun, ∇fun!, a0[[, eps,] maxiter])

Gauss-Newton nonlinear least squares. Given vectors `x` and `y`, the tries to fit parameters `a` to  a function `f` using least squares approximation:

$y = f(x, a₁, ..., aₙ)$

For more general approximations, see [`gauss_newton_fit`](@ref).

### Arguments:

  * `x` Vector with x values
  * `y` Vector with y values
  * `fun` a function that is called as `fun(x, a)` where `a` is a vector of parameters.
  * `∇fun!` A function that calculares the derivatives with respect to parameters `a`
  * `a0` Vector with the initial guesses of the parameters
  * `eps` Maximum residual for convergence
  * `maxiter` Maximum number of iterations for convergence

## Return value

A vector with the convrged array. If no convergence is achieved, the function throws an error.

## Specification of the fitting function

The function that should be fitted shoud be specified by Julia funcion with the following signature:

```julia
fun(x::T, a::AbstractVector{T}) where {T<:Number}
```

The derivatives with respect to each fitting parameter `a[i]` should have the following signature:

```julia
∇fun!(x::T, a::AbstractVector{T}, df::AbstractVector{T}) where {T<:Number}
```

No return value is expected and the derivatives are returned in argument `df`.

## Initial approximation (guess)

If the initial approximation is not good enough, divergence is possible. 

**Careful** with parameters close to 0. The initial guess should never be 0.0 because the initial value of the parameter is used as reference value for computing resiuduals.

## Convergence criteria

The argumento `maxiter` specifies the maximum number of iterations that should be carried out.  At each iteration, 

$aₖⁿ⁺¹ = aₖⁿ + δₖ$

Convergence is achieved when

$|δᵏ / aₖ⁰| < ε$

## Example

```julia
x = 1.0:10.0
a = [3.0, 2.0, 1.0]
y = a[1] + a[2]*x + a[3]*x^2
fun(x, a) = a[1] + a[2]*x + a[3]*x^2

function ∇fun!(x, a, df) 
    df[1] = 1.0
    df[2] = x
    df[3] = x^2
end

a = gauss_newton_fit(x, y, fun, ∇fun!, [0.5, 0.5, 0.5], 1e-8, 30)
```
