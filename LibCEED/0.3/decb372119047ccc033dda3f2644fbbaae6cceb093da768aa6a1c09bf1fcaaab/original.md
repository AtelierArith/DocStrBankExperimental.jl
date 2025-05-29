```
assemble_diagonal!(op::Operator, diag::CeedVector; request=RequestImmediate())
```

Overwrites a [`CeedVector`](@ref) with the diagonal of a linear [`Operator`](@ref).

!!! note "Note:"
    Currently only [`Operator`](@ref)s with a single field are supported.

