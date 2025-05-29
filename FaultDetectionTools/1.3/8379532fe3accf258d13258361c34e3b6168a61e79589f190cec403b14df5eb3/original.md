```
MDFilter <: AbstractFDDObject
```

Type for model detection filters resulted as solutions of model detection problems.

If `filter::MDFilter` is the model detection filter object,  the underlying `i`-th descriptor system model can be obtained via `filter.sys[i]` and the dimensions of the partitioned filter input vectors as  `measured outputs` and `control inputs`,   can be accessed as the integers contained in `filter.ny` and `filter.mu`, respectively.
