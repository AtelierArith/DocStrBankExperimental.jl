Extension: VK_NV_ray_tracing

Arguments:

  * `num_aab_bs::UInt32`
  * `stride::UInt32`
  * `offset::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `aabb_data::Buffer`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryAABBNV.html)

```julia
_GeometryAABBNV(
    num_aab_bs::Integer,
    stride::Integer,
    offset::Integer;
    next,
    aabb_data
) -> Vulkan._GeometryAABBNV

```
