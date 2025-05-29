Extension: VK_NV_ray_tracing

Arguments:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::GeometryDataNV`
  * `next::Any`: defaults to `C_NULL`
  * `flags::GeometryFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryNV.html)

```julia
GeometryNV(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan.GeometryDataNV;
    next,
    flags
) -> Vulkan.GeometryNV

```
