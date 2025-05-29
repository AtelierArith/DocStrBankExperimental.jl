```
freeze(dd::AbstractDict)
```

Render a dictionary immutable by converting it to a `Tuple`-backed `LittleDict`. The `Tuple`-backed `LittleDict` is faster than the `Vector`-backed `LittleDict`, particularly when the keys are all concretely typed.
