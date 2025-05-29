引数:

  * `point_clipping_behavior::PointClippingBehavior`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePointClippingProperties.html)

```julia
_PhysicalDevicePointClippingProperties(
    point_clipping_behavior::Vulkan.PointClippingBehavior;
    next
) -> Vulkan._PhysicalDevicePointClippingProperties

```
