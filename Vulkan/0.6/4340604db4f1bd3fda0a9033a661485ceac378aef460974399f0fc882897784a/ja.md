拡張: VK*EXT*opacity_micromap

引数:

  * `src::MicromapEXT`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
_CopyMicromapInfoEXT(
    src,
    dst,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMicromapInfoEXT

```
