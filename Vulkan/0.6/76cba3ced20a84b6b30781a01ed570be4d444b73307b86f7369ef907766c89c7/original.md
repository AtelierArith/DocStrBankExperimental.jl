Arguments:

  * `external_memory_properties::_ExternalMemoryProperties`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalImageFormatProperties.html)

```julia
_ExternalImageFormatProperties(
    external_memory_properties::Vulkan._ExternalMemoryProperties;
    next
) -> Vulkan._ExternalImageFormatProperties

```
