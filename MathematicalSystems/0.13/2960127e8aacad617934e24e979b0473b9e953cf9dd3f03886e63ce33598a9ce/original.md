```
isaffine(s::AbstractSystem)
```

Determines whether the dynamics of system `s` is specified by affine equations.

### Notes

An affine system is the composition of a linear system and a translation. See [`islinear(::AbstractSystem)`](@ref) for the notion of linear system adopted in this library.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`. So, if a system type allows an instance that is not affine, it returns `false` by default. For example, polynomial systems can be nonlinear; hence `isaffine` is `false`.
