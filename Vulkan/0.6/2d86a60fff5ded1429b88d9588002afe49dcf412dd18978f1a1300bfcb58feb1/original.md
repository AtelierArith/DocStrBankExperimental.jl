Extension: VK_EXT_debug_utils

Arguments:

  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `object_name::String`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectNameInfoEXT.html)

```julia
_DebugUtilsObjectNameInfoEXT(
    object_type::Vulkan.ObjectType,
    object_handle::Integer;
    next,
    object_name
) -> Vulkan._DebugUtilsObjectNameInfoEXT

```
