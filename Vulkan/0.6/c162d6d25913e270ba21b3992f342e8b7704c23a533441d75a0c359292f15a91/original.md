High-level wrapper for VkImageSubresourceLayers.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresourceLayers.html)

```julia
struct ImageSubresourceLayers <: Vulkan.HighLevelStruct
```

  * `aspect_mask::Vulkan.ImageAspectFlag`
  * `mip_level::UInt32`
  * `base_array_layer::UInt32`
  * `layer_count::UInt32`
