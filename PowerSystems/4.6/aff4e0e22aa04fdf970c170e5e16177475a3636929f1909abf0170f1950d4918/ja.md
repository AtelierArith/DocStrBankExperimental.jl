```julia
iterate_supplemental_attributes(
    sys::PowerSystems.System
) -> Base.Iterators.Flatten{Base.Generator{Base.ValueIterator{Dict{DataType, Dict{Base.UUID, <:InfrastructureSystems.SupplementalAttribute}}}, InfrastructureSystems.var"#110#111"}}

```

すべての補足属性を反復処理します。

# 例

```julia
for supplemental_attribute in iterate_supplemental_attributes(sys)
    @show supplemental_attribute
end
```

参照: [`get_supplemental_attributes`](@ref)
