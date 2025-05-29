```
FDFilter <: AbstractFDDObject
```

Type for fault detection filters resulted as solutions of fault detection problems.

If `filter::FDFilter` is the fault detection filter object, the underlying descriptor system model can be obtained via `filter.sys` and the dimensions of the partitioned filter input vectors as  `measured outputs` and `control inputs`,   can be accessed as the integers contained in `filter.ny` and `filter.mu`, respectively. The ranges of the indices of output and control inputs  can be accessed as `filter.outputs` and `filter.controls`, respectively.
