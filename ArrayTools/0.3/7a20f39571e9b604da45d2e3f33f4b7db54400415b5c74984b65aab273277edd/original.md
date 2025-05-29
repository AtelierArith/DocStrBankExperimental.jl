```
all_match(val, f, args...) -> bool
```

yields as soon as possible (short-circuit) whether `f(arg) == val` for each argument `arg` in `args...`. The returned value is `true` if there are no arguments after `f`.
