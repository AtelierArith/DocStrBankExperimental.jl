拡張: VK*EXT*opacity_micromap

引数:

  * `src::MicromapEXT`
  * `dst::_DeviceOrHostAddressKHR`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapToMemoryInfoEXT.html)

```julia
_CopyMicromapToMemoryInfoEXT(
    src,
    dst::Vulkan._DeviceOrHostAddressKHR,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMicromapToMemoryInfoEXT

```
