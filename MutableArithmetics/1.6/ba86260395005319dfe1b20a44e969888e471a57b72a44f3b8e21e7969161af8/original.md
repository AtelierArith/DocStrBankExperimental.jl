```
iszero!!(x)
```

Return a `Bool` indicating whether `x` is zero, possibly modifying `x`.

## Examples

In MathOptInterface, a `ScalarAffineFunction` may contain duplicate terms. In `Base.iszero`, duplicate terms need to be merged but the function is left with duplicates as it cannot be modified. If `iszero!!` is called instead, the function will be canonicalized in addition for checking whether it is zero.
