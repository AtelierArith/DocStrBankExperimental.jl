Extension: VK_NVX_image_view_handle

Arguments:

  * `device_address::UInt64`
  * `size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewAddressPropertiesNVX.html)

```julia
ImageViewAddressPropertiesNVX(
    device_address::Integer,
    size::Integer;
    next
) -> Vulkan.ImageViewAddressPropertiesNVX

```
