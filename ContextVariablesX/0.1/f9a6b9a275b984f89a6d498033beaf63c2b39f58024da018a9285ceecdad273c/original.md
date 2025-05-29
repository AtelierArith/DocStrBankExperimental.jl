```
ContextVar{T}
```

Context variable type.  This is the type of the object `var` created by [`@contextvar var`](@ref @contextvar).  This acts as a reference to the value stored in a task-local context.  The macro `@contextvar` is the only public API to construct this object.

!!! warning
    It is unspecified if this type is concrete or not. It may be changed to an abstract type and/or include more type parameters in the future.

