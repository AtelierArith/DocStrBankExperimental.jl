Workspace for the in-place method [`cg_lanczos_shift!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = CgLanczosShiftWorkspace(m, n, nshifts, S)
workspace = CgLanczosShiftWorkspace(A, b, nshifts)
workspace = CgLanczosShiftWorkspace(kc::KrylovConstructor, nshifts)
```
