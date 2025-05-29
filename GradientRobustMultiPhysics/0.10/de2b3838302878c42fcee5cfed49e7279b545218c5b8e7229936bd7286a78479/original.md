```
function FixedDofs(unknown_id::Int, value::Real; name::String = "")
```

constructs a FixedDofs constraint that (if assigned to a PDEDescription) ensures that the dofs are fixed to the specified values.
