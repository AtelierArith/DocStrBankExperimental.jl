```
operate(op::Function, args...)
```

Return an object equal to the result of `op(args...)` that can be mutated through the MultableArithmetics API without affecting the arguments.

By default:

  * `operate(+, x)` and `operate(+, x)` redirect to `copy_if_mutable(x)` so a mutable type `T` can return the same instance from unary operators `+(x::T) = x` and `*(x::T) = x`.
  * `operate(+, args...)` (resp. `operate(-, args...)` and `operate(*, args...)`) redirect to `+(args...)` (resp. `-(args...)` and `*(args...)`) if `length(args)` is at least 2 (or the operation is `-`).

Note that when `op` is a `Base` function whose implementation can be improved for mutable arguments, `operate(op, args...)` may have an implementation in this package relying on the MutableArithmetics API instead of redirecting to `op(args...)`. This is the case for instance:

  * for `Base.sum`,
  * for `LinearAlgebra.dot` and
  * for matrix-matrix product and matrix-vector product.

Therefore, for mutable arguments, there may be a performance advantage to call `operate(op, args...)` instead of `op(args...)`.

## Example

If for a mutable type `T`, the following is defined:

```julia
function Base.:*(a::Bool, x::T)
    return a ? x : zero(T)
end
```

then `operate(*, a, x)` will return the instance `x` whose modification will affect the argument of `operate`. Therefore, the following method need to be implemented

```julia
function MA.operate(::typeof(*), a::Bool, x::T)
    return a ? MA.mutable_copy(x) : zero(T)
end
```
