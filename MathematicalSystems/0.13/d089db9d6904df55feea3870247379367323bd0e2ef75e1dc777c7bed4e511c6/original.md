```
isblackbox(s::AbstractSystem)
```

Determines whether no specific structure is assumed for the dynamics of system `s`.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`.
