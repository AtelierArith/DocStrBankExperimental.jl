Arguments:

  * `aspect_mask::ImageAspectFlag`
  * `base_mip_level::UInt32`
  * `level_count::UInt32`
  * `base_array_layer::UInt32`
  * `layer_count::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresourceRange.html)

```julia
_ImageSubresourceRange(
    aspect_mask::Vulkan.ImageAspectFlag,
    base_mip_level::Integer,
    level_count::Integer,
    base_array_layer::Integer,
    layer_count::Integer
) -> Vulkan._ImageSubresourceRange

```
