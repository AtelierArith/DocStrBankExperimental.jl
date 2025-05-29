```
DebugEvery <: DebugAction
```

evaluate and print debug only every $i$th iteration. Otherwise no print is performed. Whether internal variables are updates is determined by `always_update`.

This method does not perform any print itself but relies on it's children's print.

It also sets the subsolvers active parameter, see |`DebugWhenActive`}(#ref). Here, the `activattion_offset` can be used to specify whether it refers to *this* iteration, the `i`th, when this call is *before* the iteration, then the offset should be 0, for the *next* iteration, that is if this is called *after* an iteration, it has to be set to 1. Since usual debug is happening after the iteration, 1 is the default.

# Constructor

```
DebugEvery(d::DebugAction, every=1, always_update=true, activation_offset=1)
```
