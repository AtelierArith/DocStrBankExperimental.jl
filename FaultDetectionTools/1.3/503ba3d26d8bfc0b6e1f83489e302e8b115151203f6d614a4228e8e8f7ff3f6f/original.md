```
FDFilterIF <: AbstractFDDObject
```

Type for the internal form of fault detection filters resulted as solutions of fault detection problems.

If `filter::FDFilterIF` is the fault detection filter internal form object,  the underlying descriptor system model can be obtained via `filter.sys` and the dimensions of the control, disturbance, fault, noise and auxiliary vectors are contained in the integers `filter.mu`, `filter.md`, `filter.mf`, `filter.mw` and `filter.ma`, respectively.  The ranges of indices of control, disturbance, fault, noise and auxiliary inputs can be accessed as `filter.controls`, `filter.disturbances`, `filter.faults`, `filter.noise` and `filter.aux`, respectively.
