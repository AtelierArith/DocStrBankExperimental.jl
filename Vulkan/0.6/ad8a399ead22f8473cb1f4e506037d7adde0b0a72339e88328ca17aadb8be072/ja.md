引数:

  * `multiview::Bool`
  * `multiview_geometry_shader::Bool`
  * `multiview_tessellation_shader::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiviewFeatures.html)

```julia
PhysicalDeviceMultiviewFeatures(
    multiview::Bool,
    multiview_geometry_shader::Bool,
    multiview_tessellation_shader::Bool;
    next
) -> Vulkan.PhysicalDeviceMultiviewFeatures

```
