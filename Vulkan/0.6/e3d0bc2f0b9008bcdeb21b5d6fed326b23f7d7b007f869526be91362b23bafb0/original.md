Arguments:

  * `max_multiview_view_count::UInt32`
  * `max_multiview_instance_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiviewProperties.html)

```julia
_PhysicalDeviceMultiviewProperties(
    max_multiview_view_count::Integer,
    max_multiview_instance_index::Integer;
    next
) -> Vulkan._PhysicalDeviceMultiviewProperties

```
