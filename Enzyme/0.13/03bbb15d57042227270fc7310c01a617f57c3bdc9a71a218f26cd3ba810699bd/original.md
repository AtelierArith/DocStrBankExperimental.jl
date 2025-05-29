```
unsafe_to_pointer
```

!!! warning
    Assumes that `val` is globally rooted and pointer to it can be leaked. Prefer `pointer_from_objref`. Only use inside Enzyme.jl should be for Types.

