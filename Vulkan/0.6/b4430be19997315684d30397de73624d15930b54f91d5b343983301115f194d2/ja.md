拡張: VK*EXT*opacity_micromap

引数:

  * `src::MicromapEXT`
  * `dst::DeviceOrHostAddressKHR`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapToMemoryInfoEXT.html)

```julia
CopyMicromapToMemoryInfoEXT(
    src::Vulkan.MicromapEXT,
    dst::Vulkan.DeviceOrHostAddressKHR,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMicromapToMemoryInfoEXT

```
