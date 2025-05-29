```julia
get_patches(
    model::EasyABM.AbstractSpaceModel
) -> Base.Generator{_A, typeof(identity)} where _A

```

与えられた条件を満たすパッチを返します。
