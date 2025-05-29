Workspace for the in-place method [`minres!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = MinresWorkspace(m, n, S; window = 5)
workspace = MinresWorkspace(A, b; window = 5)
workspace = MinresWorkspace(kc::KrylovConstructor; window = 5)
```
