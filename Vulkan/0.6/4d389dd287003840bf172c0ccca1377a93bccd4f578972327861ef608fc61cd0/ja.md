拡張: VK*EXT*debug_marker

引数:

  * `object_type::DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `tag_name::UInt64`
  * `tag_size::UInt`
  * `tag::Ptr{Cvoid}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectTagInfoEXT.html)

```julia
DebugMarkerObjectTagInfoEXT(
    object_type::Vulkan.DebugReportObjectTypeEXT,
    object::Integer,
    tag_name::Integer,
    tag_size::Integer,
    tag::Ptr{Nothing};
    next
) -> Vulkan.DebugMarkerObjectTagInfoEXT

```
