VkDeviceQueueCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueCreateInfo.html)

```julia
struct DeviceQueueCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DeviceQueueCreateFlag`
  * `queue_family_index::UInt32`
  * `queue_priorities::Vector{Float32}`
