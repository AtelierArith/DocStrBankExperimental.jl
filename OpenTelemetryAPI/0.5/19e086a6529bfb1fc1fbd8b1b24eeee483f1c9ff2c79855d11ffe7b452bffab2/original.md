```
attributes(s::AbstractSpan)
```

A [`BoundedAttributes`](@ref) is expected.

!!! warning
    Do not modify the returned attributes directly. Users should always modify attributes through `(s::AbstractSpan)[key]=val` because it will check the `is_recording(s)` first.

