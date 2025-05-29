拡張: VK*EXT*debug_marker

引数:

  * `object_type::DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `object_name::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectNameInfoEXT.html)

```julia
_DebugMarkerObjectNameInfoEXT(
    object_type::Vulkan.DebugReportObjectTypeEXT,
    object::Integer,
    object_name::AbstractString;
    next
) -> Vulkan._DebugMarkerObjectNameInfoEXT

```
