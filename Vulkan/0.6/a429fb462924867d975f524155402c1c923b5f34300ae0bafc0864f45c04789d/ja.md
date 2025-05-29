VkDeviceCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceCreateInfo.html)

```julia
struct DeviceCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `queue_create_infos::Vector{Vulkan.DeviceQueueCreateInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `enabled_features::Union{Ptr{Nothing}, Vulkan.PhysicalDeviceFeatures}`
