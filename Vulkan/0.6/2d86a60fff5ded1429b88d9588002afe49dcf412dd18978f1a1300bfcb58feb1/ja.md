拡張: VK*EXT*debug_utils

引数:

  * `object_type::ObjectType`
  * `object_handle::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `object_name::String`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsObjectNameInfoEXT.html)

```julia
_DebugUtilsObjectNameInfoEXT(
    object_type::Vulkan.ObjectType,
    object_handle::Integer;
    next,
    object_name
) -> Vulkan._DebugUtilsObjectNameInfoEXT

```
