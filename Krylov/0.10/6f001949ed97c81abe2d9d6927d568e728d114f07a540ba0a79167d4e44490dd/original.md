Workspace for the in-place method [`block_gmres!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = BlockGmresWorkspace(m, n, p, SV, SM; memory = 5)
workspace = BlockGmresWorkspace(A, B; memory = 5)
```

`memory` is set to `div(n,p)` if the value given is larger than `div(n,p)`.
