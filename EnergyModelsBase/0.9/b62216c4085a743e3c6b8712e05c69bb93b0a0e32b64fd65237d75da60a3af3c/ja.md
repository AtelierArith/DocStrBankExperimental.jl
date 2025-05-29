```
process_emissions(data::EmissionsData)
process_emissions(data::EmissionsData{T}, p::ResourceEmit)
process_emissions(data::EmissionsData{T}, p:ResourceEmit, t)
```

指定された[`EmissionsData`](@ref) `data`のプロセス排出を持つ[`ResourceEmit`](@ref)を返します。

[`ResourceEmit`](@ref) `p`が指定されている場合、排出が`Float64`として提供されている場合は`TimeProfile`（値が提供されていない場合は`FixedProfile(0)`）としてプロセス排出を返します。

[`ResourceEmit`](@ref) `p`と運用期間`t`が指定されている場合、指定された`ResourceEmit` `p`のプロセス排出がない場合は0を返します。
