```
function ExtendableGrids.interpolate!(target::FEVectorBlock,
     source::UserData{AbstractDataFunction};
     items = [],
     time = 0)
```

Interpolates the given source into the finite element space assigned to the target FEVectorBlock. The optional time argument is only used if the source depends on time.
