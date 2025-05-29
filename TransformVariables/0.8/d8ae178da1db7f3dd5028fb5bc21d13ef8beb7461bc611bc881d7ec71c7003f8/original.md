```julia
value_and_logjac_forwarddiff(
    f,
    x;
    flatten,
    handleNaN,
    chunk,
    cfg
)

```

Calculate the value and the log Jacobian determinant of `f` at `x`. `flatten` is used to get a vector out of the result that makes `f` a bijection.
