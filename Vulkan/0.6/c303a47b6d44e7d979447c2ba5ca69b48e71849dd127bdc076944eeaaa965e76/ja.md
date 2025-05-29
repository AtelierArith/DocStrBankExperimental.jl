引数:

  * `multiview::Bool`
  * `multiview_geometry_shader::Bool`
  * `multiview_tessellation_shader::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiviewFeatures.html)

```julia
_PhysicalDeviceMultiviewFeatures(
    multiview::Bool,
    multiview_geometry_shader::Bool,
    multiview_tessellation_shader::Bool;
    next
) -> Vulkan._PhysicalDeviceMultiviewFeatures

```
