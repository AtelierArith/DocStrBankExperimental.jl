```
value(T = Any, p)
```

If `p` is logically equivalent to a constant, return that constant's value wrapped in `Some`. Otherwise, return `nothing`.

Values wrapped in `Some` can be unwrapped using the `something` function.

!!! tip
    To reduce compilation latency, constants do not store the type of the wrapped value. Therefore, the type of this value cannot be inferred and can result in run-time dispatch. If this type is known at compile-time, pass it as the first parameter. See also the performance tip to [Annotate values taken from untyped locations](https://docs.julialang.org/en/v1/manual/performance-tips/#Annotate-values-taken-from-untyped-locations).


# Examples

```jldoctest
julia> @atomize value(p)

julia> @atomize value($1)
Some(1)

julia> @atomize something(value(Int, $2))
2
```
