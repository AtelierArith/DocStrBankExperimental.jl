```
File(io::IO, header::FileHeader, signals)
```

Convenience constructor that allows passing an arbitrary collection of `Signal`s and/or `AnnotationsSignal`s.

!!! note
    This method creates a copy of the *container*, but not the elements. In other words, it creates a new `Vector{Union{Signal{T},AnnotationsSignal}}` and populates it with the contents of `signals`.

