VkQueueFamilyPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyProperties.html)

```julia
struct QueueFamilyProperties <: Vulkan.HighLevelStruct
```

  * `queue_flags::Vulkan.QueueFlag`
  * `queue_count::UInt32`
  * `timestamp_valid_bits::UInt32`
  * `min_image_transfer_granularity::Vulkan.Extent3D`
