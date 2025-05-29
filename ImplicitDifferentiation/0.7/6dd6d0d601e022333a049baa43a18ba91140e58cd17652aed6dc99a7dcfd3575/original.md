```
ImplicitFunction
```

Wrapper for an implicit function defined by a *solver* and a set of *conditions* which the solution satisfies.

An `ImplicitFunction` object behaves like a function, with the following signature:

```
y, z = (implicit::ImplicitFunction)(x, args...)
```

The first output `y` is differentiable with respect to the first argument `x`, while the second output `z` (a byproduct of the solve) and the following positional arguments `args` are considered constant.

When a derivative is queried, the Jacobian of `y(x)` is computed using the implicit function theorem applied to the conditions `c(x, y)` (we ignore `z` for concision):

```
∂₂c(x, y(x)) * ∂y(x) = -∂₁c(x, y(x))
```

This requires solving a linear system `A * J = -B` where `A = ∂₂c`, `B = ∂₁c` and `J = ∂y`.

# Constructor

```
ImplicitFunction(
    solver,
    conditions,
    linear_solver=KrylovLinearSolver(),
    representation=OperatorRepresentation(),
    backend=nothing,
    preparation=nothing,
    input_example=nothing,
)
```

## Positional arguments

  * `solver`: a callable returning `(x, args...) -> (y, z)` where `z` is an arbitrary byproduct of the solve. Both `x` and `y` must be subtypes of `AbstractArray`, while `z` and `args` can be anything.
  * `conditions`: a callable returning a vector of optimality conditions `(x, y, z, args...) -> c`, must be compatible with automatic differentiation

## Keyword arguments

  * `linear_solver`: a callable to solve linear systems with two required methods, one for `(A, b)` (single solve) and one for `(A, B)` (batched solve) (defaults to [`KrylovLinearSolver`](@ref))
  * `representation`: either [`MatrixRepresentation`](@ref) or [`OperatorRepresentation`](@ref)
  * `backend::AbstractADType`: either `nothing` or an object from [ADTypes.jl](https://github.com/SciML/ADTypes.jl) dictating how how the conditions will be differentiated
  * `preparation`: either `nothing` or a mode object from [ADTypes.jl](https://github.com/SciML/ADTypes.jl): `ADTypes.ForwardMode()`, `ADTypes.ReverseMode()` or `ADTypes.ForwardOrReverseMode()`
  * `input_example`: either `nothing` or a tuple `(x, args...)` used to prepare differentiation
