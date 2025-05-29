```julia
coffset(FES::ExtendableFEMBase.FESpace) -> Int64

```

returns the offset between the degrees of freedom of each component (i.e. the number of scalar degrees of freedom that influence a component, vector-valued degrees of freedom are stored at the end).
