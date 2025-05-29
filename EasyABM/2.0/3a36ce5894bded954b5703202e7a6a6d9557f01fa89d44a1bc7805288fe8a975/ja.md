```julia
get_patches(
    model::EasyABM.AbstractSpaceModel,
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#29#30"{_A, <:Function} where _A), I<:(Base.Generator{_A, typeof(identity)} where _A)}

```

与えられた条件を満たすパッチを返します。
