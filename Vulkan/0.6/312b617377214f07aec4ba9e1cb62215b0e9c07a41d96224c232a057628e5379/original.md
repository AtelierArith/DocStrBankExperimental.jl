Extension: VK_EXT_physical_device_drm

Arguments:

  * `has_primary::Bool`
  * `has_render::Bool`
  * `primary_major::Int64`
  * `primary_minor::Int64`
  * `render_major::Int64`
  * `render_minor::Int64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDrmPropertiesEXT.html)

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
