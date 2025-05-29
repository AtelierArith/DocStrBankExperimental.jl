Represents a generalized affine operation (`w = A * v + B * b`) that may be applied to an `AbstractVecOrMat`. The user-provided update functions, `update_func[!]` update the `AbstractVecOrMat` `b`, and are called during operator evaluation (`L([w,], v, u, p, t)`), or by calls to `update_coefficients[!](L, u, p, t)`. The update functions are assumed to have the syntax

```
update_func(b::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_b
```

or

```
update_func!(b::AbstractVecOrMat, u ,p , t; <accepted kwargs>) -> [modifies b]
```

and `B`, `b` are expected to have an appropriate size so that `A * v + B * b` makes sense. Specifically, `size(A, 1) == size(B, 1)`, and `size(v, 2) == size(b, 2)`.

The set of keyword-arguments accepted by `update_func[!]` must be provided to `AffineOperator` via the kwarg `accepted_kwargs` as a tuple of `Symbol`s. `kwargs` cannot be passed down to `update_func[!]` if `accepted_kwargs` are not provided.

# Example

```
v = rand(4)
u = rand(4)
p = rand(4)
t = rand()

A = MatrixOperator(rand(4, 4))
B = MatrixOperator(rand(4, 4))

vec_update_func = (b, u, p, t) -> p .* u * t
L = AffineOperator(A, B, zero(4); update_func = vec_update_func)
L = cache_operator(M, v)

# update L and evaluate
w = L(v, u, p, t) # == A * v + B * (p .* u * t)
```
