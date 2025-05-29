```
assemble_diagonal!(op::Operator, diag::CeedVector; request=RequestImmediate())
```

Adds the diagonal of a linear [`Operator`](@ref) to the given [`CeedVector`](@ref).

!!! note "Note:"
    Currently only [`Operator`](@ref)s with a single field are supported.

