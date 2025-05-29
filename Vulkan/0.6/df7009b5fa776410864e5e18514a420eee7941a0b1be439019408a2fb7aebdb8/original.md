Extension: VK_EXT_4444_formats

Arguments:

  * `format_a4r4g4b4::Bool`
  * `format_a4b4g4r4::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevice4444FormatsFeaturesEXT.html)

```julia
_PhysicalDevice4444FormatsFeaturesEXT(
    format_a4r4g4b4::Bool,
    format_a4b4g4r4::Bool;
    next
) -> Vulkan._PhysicalDevice4444FormatsFeaturesEXT

```
