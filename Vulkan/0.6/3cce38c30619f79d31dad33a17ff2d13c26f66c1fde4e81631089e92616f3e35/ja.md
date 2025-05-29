拡張: VK*NV*ray_tracing

引数:

  * `num_aab_bs::UInt32`
  * `stride::UInt32`
  * `offset::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `aabb_data::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryAABBNV.html)

```julia
_GeometryAABBNV(
    num_aab_bs::Integer,
    stride::Integer,
    offset::Integer;
    next,
    aabb_data
) -> Vulkan._GeometryAABBNV

```
