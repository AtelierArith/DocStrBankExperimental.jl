Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::MicromapEXT`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
_CopyMicromapInfoEXT(
    src,
    dst,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan._CopyMicromapInfoEXT

```
