引数:

  * `max_multiview_view_count::UInt32`
  * `max_multiview_instance_index::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiviewProperties.html)

```julia
PhysicalDeviceMultiviewProperties(
    max_multiview_view_count::Integer,
    max_multiview_instance_index::Integer;
    next
) -> Vulkan.PhysicalDeviceMultiviewProperties

```
