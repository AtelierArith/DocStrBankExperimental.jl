```
MDModel <: AbstractFDDObject
```

Type for component synthesis models employed to solve model detection problems.

If `sysc::MDModel` is a component synthesis model object, the underlying descriptor system model can be obtained via `sysc.sys` and the dimensions of the control, disturbance, noise and auxiliary vectors are contained in the integers `sysm.mu`, `sysm.md`, `sysm.mw` and `sysm.ma`, respectively.
