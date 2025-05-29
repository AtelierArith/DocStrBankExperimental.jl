```
MDFilterIF <: AbstractFDDObject
```

Type for the internal form of model detection filters resulted as solutions of model detection problems.

If `filter::MDFilterIF` is the model detection filter internal form object,  the underlying `(i,j)`-th descriptor system model can be obtained via `filter.sys[i,j]` and the corresponding dimensions of control, disturbance, fault, noise and auxiliary input vectors are contained in  `sysm.mu`, `sysm.md[j]`, `sysm.mw[j]` and `sysm.ma[j]`, respectively.  
