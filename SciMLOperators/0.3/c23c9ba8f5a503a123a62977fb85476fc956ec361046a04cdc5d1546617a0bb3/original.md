```julia
ScalarOperator(val; update_func, accepted_kwargs)

```

Represents a linear scaling operator that may be applied to a `Number`, or an `AbstractArray` subtype. Its state is updated by the user-provided `update_func` during operator evaluation (`L([v,] u, p, t)`), or by calls to `update_coefficients[!]`. Both recursively call the update function, `update_func` which is assumed to have the signature:

```
update_func(oldval::Number, u, p, t; <accepted kwargs>) -> newval
```

The set of keyword-arguments accepted by `update_func` must be provided to `ScalarOperator` via the kwarg `accepted_kwargs` as a tuple of `Symbol`s. `kwargs` cannot be passed down to `update_func` if `accepted_kwargs` are not provided.

!!! warning
    The user-provided `update_func[!]` must not use `u` in its computation. Positional argument `(u, p, t)` to `update_func[!]` are passed down by `update_coefficients[!](L, u, p, t)`, where `u` is the input-vector to the composite `AbstractSciMLOperator`. For that reason, the values of `u`, or even shape, may not correspond to the input expected by `update_func[!]`. If an operator's state depends on its input vector, then it is, by definition, a nonlinear operator. We recommend sticking such nonlinearities in `FunctionOperator.` This topic is further discussed in (this issue)[https://github.com/SciML/SciMLOperators.jl/issues/159].


# Interface

Lazy scalar algebra is defined for `AbstractSciMLScalarOperator`s. The interface supports lazy addition, subtraction, multiplication and division.

# Example

```
v = zero(4)
u = rand(4)
p = nothing
t = 0.0

val_update = (a, u, p, t; scale = 0.0) -> copy(scale)
α = ScalarOperator(0.0; update_func = val_update; accepted_kwargs = (:scale,))
β = 2 * α + 3 / α

# update L out-of-place, and evaluate
β(u, p, t; scale = 1.0)

# update L in-place and evaluate
β(v, u, p, t; scale = 1.0)
```
