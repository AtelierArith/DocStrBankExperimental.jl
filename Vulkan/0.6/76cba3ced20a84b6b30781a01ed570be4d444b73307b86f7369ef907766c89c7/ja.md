引数:

  * `external_memory_properties::_ExternalMemoryProperties`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalImageFormatProperties.html)

```julia
_ExternalImageFormatProperties(
    external_memory_properties::Vulkan._ExternalMemoryProperties;
    next
) -> Vulkan._ExternalImageFormatProperties

```
