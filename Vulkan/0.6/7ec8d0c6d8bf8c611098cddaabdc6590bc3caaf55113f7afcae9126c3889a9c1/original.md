High-level wrapper for VkImageSubresourceRange.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresourceRange.html)

```julia
struct ImageSubresourceRange <: Vulkan.HighLevelStruct
```

  * `aspect_mask::Vulkan.ImageAspectFlag`
  * `base_mip_level::UInt32`
  * `level_count::UInt32`
  * `base_array_layer::UInt32`
  * `layer_count::UInt32`
