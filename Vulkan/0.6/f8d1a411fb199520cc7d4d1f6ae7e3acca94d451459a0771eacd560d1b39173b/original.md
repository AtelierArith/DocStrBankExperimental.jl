Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::DeviceOrHostAddressConstKHR`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
CopyMemoryToMicromapInfoEXT(
    src::Vulkan.DeviceOrHostAddressConstKHR,
    dst::Vulkan.MicromapEXT,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMemoryToMicromapInfoEXT

```
