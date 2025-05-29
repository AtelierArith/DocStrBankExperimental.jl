拡張: VK*EXT*opacity_micromap

引数:

  * `src::MicromapEXT`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
CopyMicromapInfoEXT(
    src::Vulkan.MicromapEXT,
    dst::Vulkan.MicromapEXT,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMicromapInfoEXT

```
