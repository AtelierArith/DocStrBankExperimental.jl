```
@infiltrate
@infiltrate condition::Bool
```

`@infiltrate` sets an infiltration point (or breakpoint).

When the infiltration point is hit, it will drop you into an interactive REPL session that lets you inspect local variables and the call stack as well as execute arbitrary statements in the context of the current functions module.

This macro also accepts an optional argument `cond` that must evaluate to a boolean, and then this macro will serve as a "conditional breakpoint", which starts inspections only when its condition is `true`. For example:

```
@infiltrate false # does not infiltrate
```
