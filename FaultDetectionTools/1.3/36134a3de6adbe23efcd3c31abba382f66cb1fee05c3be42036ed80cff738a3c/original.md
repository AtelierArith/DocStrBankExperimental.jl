```
FDIFilter <: AbstractFDDObject
```

Type for fault detection and isolation filters resulted as solutions of fault detection and isolation problems.

If `filter::FDIFilter` is the fault detection and isolation filter object,  the underlying `i`-th descriptor system model can be obtained via `filter.sys[i]` and the dimensions of the partitioned filter input vectors as  `measured outputs` and `control inputs`,   can be accessed as the integers contained in `filter.ny` and `filter.mu`, respectively. The ranges of the indices of output and control inputs  can be accessed as `filter.outputs` and `filter.controls`, respectively.
