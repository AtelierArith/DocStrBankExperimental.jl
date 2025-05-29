```
isnoisy(s::AbstractSystem)
```

Determines if the dynamics of system `s` contains a noise term `w`.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`.
