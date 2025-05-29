Workspace for the in-place method [`qmr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = QmrWorkspace(m, n, S)
workspace = QmrWorkspace(A, b)
workspace = QmrWorkspace(kc::KrylovConstructor)
```
