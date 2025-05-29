```
EasyRanges.stretch(a, b)
```

yields the result of stretching `a` by amount `b`. This is equivalent to the expression `a ± b` in [`@range`](@ref) macro.

Foreign packages may extend `EasyRanges.stretch(a, b)` for specific types of `a` and `b`.
