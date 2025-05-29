Arguments:

  * `aspect_mask::ImageAspectFlag`
  * `mip_level::UInt32`
  * `base_array_layer::UInt32`
  * `layer_count::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageSubresourceLayers.html)

```julia
_ImageSubresourceLayers(
    aspect_mask::Vulkan.ImageAspectFlag,
    mip_level::Integer,
    base_array_layer::Integer,
    layer_count::Integer
) -> Vulkan._ImageSubresourceLayers

```
