Workspace for the in-place method [`cg!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = CgWorkspace(m, n, S)
workspace = CgWorkspace(A, b)
workspace = CgWorkspace(kc::KrylovConstructor)
```
