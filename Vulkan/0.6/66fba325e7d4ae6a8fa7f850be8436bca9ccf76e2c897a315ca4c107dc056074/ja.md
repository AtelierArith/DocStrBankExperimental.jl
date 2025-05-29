拡張: VK*NV*ray_tracing

引数:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::GeometryDataNV`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::GeometryFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryNV.html)

```julia
GeometryNV(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan.GeometryDataNV;
    next,
    flags
) -> Vulkan.GeometryNV

```
