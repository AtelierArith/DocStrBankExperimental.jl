```
@transform_ints(type="")
```

Rotate FCIDump integrals using [`WfOptions.orb`](@ref ECInfos.WfOptions) as transformation    matrices.

The orbitals are read from [`WfOptions.orb`](@ref ECInfos.WfOptions).   If type is one of [bo, BO, bi-orthogonal, Bi-orthogonal, biorth, biorthogonal, Biorthogonal],    the bi-orthogonal orbitals are used and the left transformation matrix is   read from [`WfOptions.orb`](@ref ECInfos.WfOptions)*[`WfOptions.left`](@ref ECInfos.WfOptions).
