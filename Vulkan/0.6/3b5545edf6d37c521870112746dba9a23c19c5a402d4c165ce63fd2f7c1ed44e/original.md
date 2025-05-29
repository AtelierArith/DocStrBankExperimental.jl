High-level wrapper for VkImageViewCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewCreateInfo.html)

```julia
struct ImageViewCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.ImageViewCreateFlag`
  * `image::Vulkan.Image`
  * `view_type::Vulkan.ImageViewType`
  * `format::Vulkan.Format`
  * `components::Vulkan.ComponentMapping`
  * `subresource_range::Vulkan.ImageSubresourceRange`
