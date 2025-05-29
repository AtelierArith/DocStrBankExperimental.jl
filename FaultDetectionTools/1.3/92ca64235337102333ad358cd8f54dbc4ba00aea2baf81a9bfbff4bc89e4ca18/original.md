```
FDIModel <: AbstractFDDObject
```

Type for synthesis models employed to solve fault detection and isolation problems.

If `sysf::FDIModel` is the synthesis model object, the underlying descriptor system model can be obtained via `sysf.sys` and the dimensions of the control, disturbance, fault, noise and auxiliary vectors are contained in the integers `sysf.mu`, `sysf.md`, `sysf.mf`, `sysf.mw` and `sysf.ma`, respectively. The ranges of indices of control, disturbance, fault, noise and auxiliary inputs can be accessed as `sysf.controls`, `sysf.disturbances`, `sysf.faults`, `sysf.noise` and `sysf.aux`, respectively.
