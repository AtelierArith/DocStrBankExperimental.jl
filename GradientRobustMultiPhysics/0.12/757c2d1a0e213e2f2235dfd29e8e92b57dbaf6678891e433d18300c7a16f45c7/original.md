```
function FixedIntegralMean(unknown_id::Int, value::Real; name::String = "")
```

constructs a FixedIntegralMean constraint that (if assigned to a PDEDescription) ensures that the unknown with the specified id has an integral mean value.
