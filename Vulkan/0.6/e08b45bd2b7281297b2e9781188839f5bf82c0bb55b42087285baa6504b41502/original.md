Extension: VK_EXT_debug_marker

Arguments:

  * `object_type::DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `object_name::String`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugMarkerObjectNameInfoEXT.html)

```julia
DebugMarkerObjectNameInfoEXT(
    object_type::Vulkan.DebugReportObjectTypeEXT,
    object::Integer,
    object_name::AbstractString;
    next
) -> Vulkan.DebugMarkerObjectNameInfoEXT

```
