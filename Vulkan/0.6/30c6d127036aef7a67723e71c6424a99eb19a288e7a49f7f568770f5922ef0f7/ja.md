VkDeviceQueueInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueInfo2.html)

```julia
struct DeviceQueueInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DeviceQueueCreateFlag`
  * `queue_family_index::UInt32`
  * `queue_index::UInt32`
