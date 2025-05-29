```julia
DiagonalOperator(
    diag;
    update_func,
    update_func!,
    accepted_kwargs
)

```

Represents an elementwise scaling (diagonal-scaling) operation that may be applied to an `AbstractVecOrMat`. When `diag` is an `AbstractVector` of length N, `L = DiagonalOperator(diag, ...)` can be applied to `AbstractArray`s with `size(u, 1) == N`. Each column of the `v` will be scaled by `diag`, as in `LinearAlgebra.Diagonal(diag) * v`.

When `diag` is a multidimensional array, `L = DiagonalOperator(diag, ...)` forms an operator of size `(N, N)` where `N = size(diag, 1)` is the leading length of `diag`. `L` then is the elementwise-scaling operation on arrays of `length(v) = length(diag)` with leading length `size(u, 1) = N`.

Its state is updated by the user-provided `update_func` during operator evaluation (`L([w,], v, u, p, t)`), or by calls to `update_coefficients[!](L, u, p, t)`. Both recursively call the `update_function`, `update_func` which is assumed to have the signature

```
update_func(diag::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_diag
```

or

```
update_func!(diag::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> [modifies diag]
```

The set of keyword-arguments accepted by `update_func[!]` must be provided to `MatrixOperator` via the kwarg `accepted_kwargs` as a tuple of `Symbol`s. `kwargs` cannot be passed down to `update_func[!]` if `accepted_kwargs` are not provided.

!!! warning
    The user-provided `update_func[!]` must not use `u` in its computation. Positional argument `(u, p, t)` to `update_func[!]` are passed down by `update_coefficients[!](L, u, p, t)`, where `u` is the input-vector to the composite `AbstractSciMLOperator`. For that reason, the values of `u`, or even shape, may not correspond to the input expected by `update_func[!]`. If an operator's state depends on its input vector, then it is, by definition, a nonlinear operator. We recommend sticking such nonlinearities in `FunctionOperator.` This topic is further discussed in (this issue)[https://github.com/SciML/SciMLOperators.jl/issues/159].


# Example
