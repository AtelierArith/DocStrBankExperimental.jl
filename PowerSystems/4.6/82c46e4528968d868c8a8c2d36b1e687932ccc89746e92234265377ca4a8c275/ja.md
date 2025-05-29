```julia
get_supplemental_attributes(
    filter_func::Function,
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    sys::PowerSystems.System
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:InfrastructureSystems.SupplementalAttribute, I<:(Vector)}

```

補足属性のイテレータを返します。Tは具体的または抽象的であり得ます。配列が必要な場合は、結果に対してcollectを呼び出してください。

# 例

```julia
iter = get_supplemental_attributes(GeometricDistributionForcedOutage, sys)
iter = get_supplemental_attributes(Outage, sys)
iter = get_supplemental_attributes(x -> get_mean_time_to_recovery(x) ==  >= 0.5, GeometricDistributionForcedOutage, sys)
outages = get_supplemental_attributes(GeometricDistributionForcedOutage, sys) do outage
    get_mean_time_to_recovery(x) ==  >= 0.5
end
outages = collect(get_supplemental_attributes(GeometricDistributionForcedOutage, sys))
```

参照: [`iterate_supplemental_attributes`](@ref)
