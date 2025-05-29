```
@?(expr)
```

Propagate a `Result` with `Err` value to the outer function. Evaluate `expr`, which should return a `Result`. If it contains an `Ok` value `x`, evaluate to the unwrapped value `x`. Else, evaluates to `return Err(x)`.

# Examples

```jldoctest
julia> (f(x::Option{T})::Option{T}) where T = Ok(@?(x) + one(T));

julia> f(some(1.0)), f(none(Int))
(some(2.0), none(Int64))
```
