Workspace for the in-place method [`cg_lanczos!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = CgLanczosWorkspace(m, n, S)
workspace = CgLanczosWorkspace(A, b)
workspace = CgLanczosWorkspace(kc::KrylovConstructor)
```
