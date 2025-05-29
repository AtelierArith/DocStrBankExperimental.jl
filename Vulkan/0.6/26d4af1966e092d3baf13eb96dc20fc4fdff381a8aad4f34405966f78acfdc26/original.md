Extension: VK_EXT_debug_utils

Arguments:

  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `tag_name::UInt64`
  * `tag_size::UInt`
  * `tag::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectTagInfoEXT.html)

```julia
_DebugUtilsObjectTagInfoEXT(
    object_type::Vulkan.ObjectType,
    object_handle::Integer,
    tag_name::Integer,
    tag_size::Integer,
    tag::Ptr{Nothing};
    next
) -> Vulkan._DebugUtilsObjectTagInfoEXT

```
