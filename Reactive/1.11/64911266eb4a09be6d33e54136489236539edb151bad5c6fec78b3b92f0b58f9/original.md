```
filterwhen(switch::Signal{Bool}, default, input)
```

Keep updates to `input` only when `switch` is true.

If switch is false initially, the specified default value is used.
