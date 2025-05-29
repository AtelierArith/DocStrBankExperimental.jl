```
Block{T}()
Block(times::AbstractVector{DateTime}, values::AbstractVector{T})
Block(unchecked, times, values)
```

Represent some data in timeseries.

Conceptually this is a list of `(time, value)` pairs, or "knots". Times must be strictly increasing — i.e. no repeated timestamps are allowed.

The constructor `Block(times, values)` will verify that the input data satisfies this constraint, however `Block(unchecked, times, values)` will skip the checks. This is primarily intended for internal use, where the caller assumes responsibility for the validity of `times` & `values`.

!!! danger
    `TimeDag` considers instances of `Block` to be completely immutable. Thus, when working with functions that accept blocks (e.g. [`TimeDag.run_node!`](@ref)), you must not modify `times` or `values` members.

