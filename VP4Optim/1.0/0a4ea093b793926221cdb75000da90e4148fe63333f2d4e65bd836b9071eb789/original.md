```
x_changed!(::Model)
```

Informs user-defined model that `x` has changed.

## Default

  * Does nothing.

## Remarks

  * Can be used to recalculate any auxiliary model variable (such as `A`), which depends on `x`.
