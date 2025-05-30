```
@disallow_boxed_captures expr
```

Disable the effect of `@allow_boxed_captures` for any code in `expr`.

This is a dynamically scoped construct, so this effect will apply to *all* nested code inside of `expr`.

See also `@disallow_boxed_captures`
