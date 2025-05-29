```
restore!(mach::Machine)
```

Restore the state of a machine that is currently serializable but which may not be otherwise usable. For such a machine, `mach`, one has `mach.state=1`. Intended for restoring deserialized machine objects to a useable form.

For an example see [`serializable`](@ref).
