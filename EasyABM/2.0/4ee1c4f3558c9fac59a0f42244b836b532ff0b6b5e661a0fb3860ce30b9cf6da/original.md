```julia
get_patches(
    model::EasyABM.AbstractSpaceModel
) -> Base.Generator{_A, typeof(identity)} where _A

```

Returns patches satisfying the given condition.
