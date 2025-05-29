Extension: VK_EXT_image_compression_control

Arguments:

  * `device::Device`
  * `image::Image`
  * `subresource::ImageSubresource2EXT`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageSubresourceLayout2EXT.html)

```julia
get_image_subresource_layout_2_ext(
    device,
    image,
    subresource::Vulkan.ImageSubresource2EXT,
    next_types::Type...
) -> Vulkan.SubresourceLayout2EXT

```
