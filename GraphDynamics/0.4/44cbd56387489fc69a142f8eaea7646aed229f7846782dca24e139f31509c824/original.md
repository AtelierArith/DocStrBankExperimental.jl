```
combine(input1, input2)
```

When a `Subsystem` is connected to multiple other subsystems, all of the inputs sent to that `Subsystem` via the connections must be `combine`'d together into one input representing the accumulation of all of the inputs. `combine` is the function used to accumulate these inputs together at each step. Defaults to addition, but can have methods added to it for more exotic input types.
