```
gradient!(y, f, x)
```

In-place gradient (and value) of `f` at `x`.

The gradient is written to the (pre-allocated) array `y`, which should have the same shape/size as `x`.

Returns the value `f` at `x`.

See also: [`gradient`](@ref).
