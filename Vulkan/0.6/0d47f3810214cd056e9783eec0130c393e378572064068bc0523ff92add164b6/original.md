Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::MicromapEXT`
  * `dst::_DeviceOrHostAddressKHR`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapToMemoryInfoEXT.html)

```julia
_CopyMicromapToMemoryInfoEXT(
    src,
    dst::Vulkan._DeviceOrHostAddressKHR,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMicromapToMemoryInfoEXT

```
