```
OrthoMADS()
```

Return an empty OrthoMADS object. `N` must match the dimension of the problem that this stage is being given to.

OrthoMADS uses Halton sequences to generate an orthogonal basis of directiosn for the poll step. This is a deterministic process, unlike (`LTMADS`)[@ref].
