```
struct Problem
```

Program synthesis problem defined by an [`AbstractSpecification`](@ref)s. Has a name and a specification of type `T`.

!!! warning
    Please care that concrete `Problem` types with different values of `T` are never subtypes of each other.

