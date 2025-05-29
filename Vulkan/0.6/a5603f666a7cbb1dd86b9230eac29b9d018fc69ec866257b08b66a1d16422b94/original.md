Extension: VK_NV_ray_tracing

Arguments:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::_GeometryDataNV`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::GeometryFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryNV.html)

```julia
_GeometryNV(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan._GeometryDataNV;
    next,
    flags
) -> Vulkan._GeometryNV

```
