拡張: VK*EXT*opacity_micromap

引数:

  * `src::_DeviceOrHostAddressConstKHR`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
_CopyMemoryToMicromapInfoEXT(
    src::Vulkan._DeviceOrHostAddressConstKHR,
    dst,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMemoryToMicromapInfoEXT

```
