```
EasyRanges.minus(x)
EasyRanges.minus(x, y)
```

yield the result of expressions `-x` or `x - y` in [`@range`](@ref) macro.

Foreign packages may extend `EasyRanges.minus(x)` and `EasyRanges.minus(x, y)` for specific types of `x` and `y`.
