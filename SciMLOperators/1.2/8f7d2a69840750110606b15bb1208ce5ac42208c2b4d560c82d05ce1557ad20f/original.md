Represents a linear operator given by an `AbstractMatrix` that may be applied to an `AbstractVecOrMat`. Its state is updated by the user-provided `update_func` during operator evaluation (`L([w,], v, u, p, t)`), or by calls to `update_coefficients[!](L, u, p, t)`. Both recursively call the `update_function`, `update_func` which is assumed to have the signature

```
update_func(A::AbstractMatrix, u, p, t; <accepted kwargs>) -> newA
```

or

```
update_func!(A::AbstractMatrix, u, p, t; <accepted kwargs>) -> [modifies A]
```

The set of keyword-arguments accepted by `update_func[!]` must be provided to `MatrixOperator` via the kwarg `accepted_kwargs` as a tuple of `Symbol`s. `kwargs` cannot be passed down to `update_func[!]` if `accepted_kwargs` are not provided.

!!! warning
    The user-provided `update_func[!]` must not use `u` in its computation. Positional argument `(u, p, t)` to `update_func[!]` are passed down by `update_coefficients[!](L, u, p, t)`, where `u` is the input-vector to the composite `AbstractSciMLOperator`. For that reason, the values of `u`, or even shape, may not correspond to the input expected by `update_func[!]`. If an operator's state depends on its input vector, then it is, by definition, a nonlinear operator. We recommend sticking such nonlinearities in `FunctionOperator.` This topic is further discussed in (this issue)[https://github.com/SciML/SciMLOperators.jl/issues/159].


# Interface

Lazy matrix algebra is defined for `AbstractSciMLOperator`s. The Interface supports lazy addition, subtraction, multiplication, inversion, adjoints, transposes.

# Example

Out-of-place update and usage

```
v = rand(4)
u = rand(4)
p = rand(4, 4)
t = rand()

mat_update = (A, u, p, t; scale = 0.0) -> t * p
M = MatrixOperator(0.0; update_func = mat_update, accepted_kwargs = (:scale,))

L = M * M + 3I
L = cache_operator(L, v)

# update and evaluate 
w = L(v, u, p, t; scale = 1.0)

# In-place evaluation
w = similar(v)
L(w, v, u, p, t; scale = 1.0)

# In-place with scaling
β = 0.5
L(w, v, u, p, t, 2.0, β; scale = 1.0) # w = 2.0*(L*v) + 0.5*w
```

In-place update and usage

```
w = zeros(4)
v = zeros(4)
u = rand(4)
p = rand(4) # Must be non-nothing
t = rand()

mat_update! = (A, u, p, t; scale = 0.0) -> (A .= t * p * u' * scale)
M = MatrixOperator(zeros(4, 4); update_func! = mat_update!, accepted_kwargs = (:scale,))
L = M * M + 3I
L = cache_operator(L, v) 

# update L in-place and evaluate
update_coefficients!(L, u, p, t; scale = 1.0)
mul!(w, L, v)

# Or use the new interface that separates update and application
L(w, v, u, p, t; scale = 1.0)
```
