Workspace for the in-place method [`cgls_lanczos_shift!`](@ref).

The following outer constructors can be used to initialize this workspace::

```
workspace = CglsLanczosShiftWorkspace(m, n, nshifts, S)
workspace = CglsLanczosShiftWorkspace(A, b, nshifts)
workspace = CglsLanczosShiftWorkspace(kc::KrylovConstructor, nshifts)
```
