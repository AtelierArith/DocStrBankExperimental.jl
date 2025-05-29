`features`をtrueに設定した`PhysicalDeviceFeatures`オブジェクトを返します。

```jldoctest
julia> PhysicalDeviceFeatures()
PhysicalDeviceFeatures()

julia> PhysicalDeviceFeatures(:wide_lines, :sparse_binding)
PhysicalDeviceFeatures(wide_lines, sparse_binding)
```

```julia
PhysicalDeviceFeatures(features::Symbol...) -> Any

```
