```
@not_implemented(info)
```

Create a tangent that indicates that the derivative is not implemented.

The `info` should be useful information about the missing tangent for debugging.

!!! note
    This macro should be used only if the automatic differentiation would error otherwise. It is mostly useful if the function has multiple inputs or outputs, and one has worked out analytically and implemented some but not all tangents.


!!! note
    It is good practice to include a link to a GitHub issue about the missing tangent in the debugging information.

