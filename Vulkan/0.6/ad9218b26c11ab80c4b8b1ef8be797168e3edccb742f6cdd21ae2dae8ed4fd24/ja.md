拡張: VK*EXT*rasterization*order*attachment_access

引数:

  * `rasterization_order_color_attachment_access::Bool`
  * `rasterization_order_depth_attachment_access::Bool`
  * `rasterization_order_stencil_attachment_access::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT.html)

```julia
PhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT(
    rasterization_order_color_attachment_access::Bool,
    rasterization_order_depth_attachment_access::Bool,
    rasterization_order_stencil_attachment_access::Bool;
    next
) -> Vulkan.PhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT

```
