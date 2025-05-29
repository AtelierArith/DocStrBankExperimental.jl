Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::MicromapEXT`
  * `dst::DeviceOrHostAddressKHR`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapToMemoryInfoEXT.html)

```julia
CopyMicromapToMemoryInfoEXT(
    src::Vulkan.MicromapEXT,
    dst::Vulkan.DeviceOrHostAddressKHR,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMicromapToMemoryInfoEXT

```
