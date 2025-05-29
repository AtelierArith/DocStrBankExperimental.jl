```
FDIFilterIF <: AbstractFDDObject
```

Type for the internal form of fault detection and isolation filters resulted as solutions of fault detection and isolation problems.

If `filter::FDIFilterIF` is the fault detection and isolation filter internal form object,  the underlying `i`-th descriptor system model can be obtained via `filter.sys[i]` and the dimensions of the control, disturbance, fault, noise and auxiliary vectors are contained in the integers `filter.mu`, `filter.md`, `filter.mf`, `filter.mw` and `filter.ma`, respectively.  The ranges of indices of control, disturbance, fault, noise and auxiliary inputs can be accessed as `filter.controls`, `filter.disturbances`, `filter.faults`, `filter.noise` and `filter.aux`, respectively. .
