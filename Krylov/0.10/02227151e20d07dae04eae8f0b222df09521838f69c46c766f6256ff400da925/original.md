Workspace for the in-place method [`minres_qlp!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = MinresQlpWorkspace(m, n, S)
workspace = MinresQlpWorkspace(A, b)
workspace = MinresQlpWorkspace(kc::KrylovConstructor)
```
