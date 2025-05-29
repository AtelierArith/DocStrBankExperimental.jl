拡張: VK*EXT*physical*device*drm

引数:

  * `has_primary::Bool`
  * `has_render::Bool`
  * `primary_major::Int64`
  * `primary_minor::Int64`
  * `render_major::Int64`
  * `render_minor::Int64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDrmPropertiesEXT.html)

```julia
PhysicalDeviceDrmPropertiesEXT(
    has_primary::Bool,
    has_render::Bool,
    primary_major::Integer,
    primary_minor::Integer,
    render_major::Integer,
    render_minor::Integer;
    next
) -> Vulkan.PhysicalDeviceDrmPropertiesEXT

```
