```julia
update_coefficients(L, u, p, t; kwargs...)

```

Update the state of `L` based on `u`, input vector, `p` parameter object, `t`, and keyword arguments. Internally, `update_coefficients` calls the user-provided `update_func` method for every component operator in `L` with the positional arguments `(u, p, t)` and keyword arguments corresponding to the symbols provided to the operator via kwarg `accepted_kwargs`.

This method is out-of-place, i.e. fully non-mutating and `Zygote`-compatible.

!!! warning
    The user-provided `update_func[!]` must not use `u` in its computation. Positional argument `(u, p, t)` to `update_func[!]` are passed down by `update_coefficients[!](L, u, p, t)`, where `u` is the input-vector to the composite `AbstractSciMLOperator`. For that reason, the values of `u`, or even shape, may not correspond to the input expected by `update_func[!]`. If an operator's state depends on its input vector, then it is, by definition, a nonlinear operator. We recommend sticking such nonlinearities in `FunctionOperator.` This topic is further discussed in (this issue)[https://github.com/SciML/SciMLOperators.jl/issues/159].


# Example

```
using SciMLOperator

mat_update_func = (A, u, p, t; scale = 1.0) -> p * p' * scale * t

M = MatrixOperator(zeros(4,4); update_func = mat_update_func,
                   accepted_kwargs = (:state,))

L = M + IdentityOperator(4)

u = rand(4)
p = rand(4)
t = 1.0

L = update_coefficients(L, u, p, t; scale = 2.0)
L * u
```
