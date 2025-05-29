High-level wrapper for VkImageBlit2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageBlit2.html)

```julia
struct ImageBlit2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_subresource::Vulkan.ImageSubresourceLayers`
  * `src_offsets::Tuple{Vulkan.Offset3D, Vulkan.Offset3D}`
  * `dst_subresource::Vulkan.ImageSubresourceLayers`
  * `dst_offsets::Tuple{Vulkan.Offset3D, Vulkan.Offset3D}`
