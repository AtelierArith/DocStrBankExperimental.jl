Extension: VK_EXT_debug_utils

Arguments:

  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `next::Any`: defaults to `C_NULL`
  * `object_name::String`: defaults to ``

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectNameInfoEXT.html)

```julia
DebugUtilsObjectNameInfoEXT(
    object_type::Vulkan.ObjectType,
    object_handle::Integer;
    next,
    object_name
) -> Vulkan.DebugUtilsObjectNameInfoEXT

```
