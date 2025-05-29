Workspace for the in-place method [`bicgstab!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = BicgstabWorkspace(m, n, S)
workspace = BicgstabWorkspace(A, b)
workspace = BicgstabWorkspace(kc::KrylovConstructor)
```
