`features`をtrueに設定した`PhysicalDeviceVulkan12Features`オブジェクトを返します。

```jldoctest
julia> PhysicalDeviceVulkan12Features(; next = C_NULL)
PhysicalDeviceVulkan12Features(next=Ptr{Nothing}(0x0000000000000000))

julia> PhysicalDeviceVulkan12Features(:draw_indirect_count, :descriptor_binding_variable_descriptor_count)
PhysicalDeviceVulkan12Features(next=Ptr{Nothing}(0x0000000000000000), draw_indirect_count, descriptor_binding_variable_descriptor_count)
```

```julia
PhysicalDeviceVulkan12Features(
    features::Symbol...;
    next
) -> Vulkan.PhysicalDeviceVulkan12Features

```
