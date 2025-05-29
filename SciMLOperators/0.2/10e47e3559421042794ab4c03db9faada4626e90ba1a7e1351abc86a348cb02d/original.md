Represents a generalized affine operation (`v = A * u + B * b`) that may be applied to an `AbstractVecOrMat`. The user-provided update functions, `update_func[!]` update the `AbstractVecOrMat` `b`, and are called during during operator evaluation (`L([v,], u, p, t)`), or by calls to `update_coefficients[!](L, u, p, t)`. The update functions are assumped to have the syntax

```
update_func(b::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_b
```

or

```
update_func!(b::AbstractVecOrMat, u ,p , t; <accepted kwargs>) -> [modifies b]
```

and `B`, `b` are expected to have an appropriate size so that `A * u + B * b` makes sense. Specifically, `size(A, 1) == size(B, 1)`, and `size(u, 2) == size(b, 2)`.

The set of keyword-arguments accepted by `update_func[!]` must be provided to `AffineOperator` via the kwarg `accepted_kwargs` as a tuple of `Symbol`s. `kwargs` cannot be passed down to `update_func[!]` if `accepted_kwargs` are not provided.

# Example

```
u = rand(4)
p = rand(4)
t = rand()

A = MatrixOperator(rand(4, 4))
B = MatrixOperator(rand(4, 4))

vec_update_func = (b, u, p, t) -> p * t
L = AffineOperator(A, B, zero(4); update_func = vec_update_func)
L = cache_operator(M, u)

# update L and evaluate
v = L(u, p, t) # == A * u + B * (p * t)
```
