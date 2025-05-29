```
MDMModel <: AbstractFDDObject
```

Type for multiple synthesis models employed to solve model detection problems.

If `sysm::MDMModel` is the multiple synthesis model object, the underlying vector of descriptor system models can be obtained via `sysm.sys`, the common dimension of the control vectors is contained in the integer `sysm.mu`, and the dimensions of the disturbance, noise  and auxiliary input vectors for the `i`-th model `sysm.sys[i]` are contained in the `i`-th  components of the integer vectors `sysm.md`, `sysm.mw` and `sysm.ma`, respectively.
