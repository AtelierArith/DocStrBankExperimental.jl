```
function ExtendableGrids.interpolate!(target::FEVectorBlock,
     AT::Type{<:AssemblyType},
     source::UserData{AbstractDataFunction};
     items = [],
     time = 0)
```

Interpolates the given source into the finite elements space assigned to the target FEVectorBlock with the specified AssemblyType (usualy ON_CELLS). The optional time argument is only used if the source depends on time.
