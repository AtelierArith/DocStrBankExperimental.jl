Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::_DeviceOrHostAddressConstKHR`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
_CopyMemoryToMicromapInfoEXT(
    src::Vulkan._DeviceOrHostAddressConstKHR,
    dst,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMemoryToMicromapInfoEXT

```
