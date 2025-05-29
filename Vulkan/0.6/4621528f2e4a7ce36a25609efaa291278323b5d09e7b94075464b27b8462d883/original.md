Extension: VK_EXT_opacity_micromap

Arguments:

  * `src::MicromapEXT`
  * `dst::MicromapEXT`
  * `mode::CopyMicromapModeEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
CopyMicromapInfoEXT(
    src::Vulkan.MicromapEXT,
    dst::Vulkan.MicromapEXT,
    mode::Vulkan.CopyMicromapModeEXT;
    next
) -> Vulkan.CopyMicromapInfoEXT

```
