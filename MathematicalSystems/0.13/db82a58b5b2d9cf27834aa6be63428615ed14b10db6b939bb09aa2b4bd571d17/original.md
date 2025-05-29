```
iscontrolled(s::AbstractSystem)
```

Determines if the dynamics of system `s` contains a control input `u`.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`.
