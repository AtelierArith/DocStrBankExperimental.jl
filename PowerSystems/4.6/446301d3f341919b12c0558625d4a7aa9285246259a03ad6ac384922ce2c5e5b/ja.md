```julia
iterate_components(
    sys::PowerSystems.System
) -> InfrastructureSystems.FlattenIteratorWrapper{InfrastructureSystems.InfrastructureSystemsComponent, I} where I<:(Vector)

```

すべてのコンポーネントを反復処理します。

# 例

```julia
for component in iterate_components(sys)
    @show component
end
```

関連情報: [`get_components`](@ref)
