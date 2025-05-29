High-level wrapper for VkImageSubresource.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresource.html)

```julia
struct ImageSubresource <: Vulkan.HighLevelStruct
```

  * `aspect_mask::Vulkan.ImageAspectFlag`
  * `mip_level::UInt32`
  * `array_layer::UInt32`
