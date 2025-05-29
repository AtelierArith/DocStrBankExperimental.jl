```
isconstrained(s::AbstractSystem)
```

Determines if the system `s` has constraints on the state, input and noise, respectively (those that are available).

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`.
