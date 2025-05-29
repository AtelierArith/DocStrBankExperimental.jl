```
EasyRanges.shrink(a, b)
```

yields the result of shrinking `a` by amount `b`. This is equivalent to the expression `a ∓ b` in [`@range`](@ref) macro.

Foreign packages may extend `EasyRanges.shrink(a, b)` for specific types of `a` and `b`.
