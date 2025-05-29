Workspace for the in-place method [`tricg!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = TricgWorkspace(m, n, S)
workspace = TricgWorkspace(A, b)
workspace = TricgWorkspace(kc::KrylovConstructor)
```
