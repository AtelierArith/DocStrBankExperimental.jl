拡張: VK*EXT*opacity_micromap

引数:

  * `src::DeviceOrHostAddressConstKHR`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToMicromapInfoEXT.html)

```julia
CopyMemoryToMicromapInfoEXT(
    src::Vulkan.DeviceOrHostAddressConstKHR,
    dst::Vulkan.MicromapEXT,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMemoryToMicromapInfoEXT

```
