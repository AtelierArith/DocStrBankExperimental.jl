Extension: VK_EXT_rasterization_order_attachment_access

Arguments:

  * `rasterization_order_color_attachment_access::Bool`
  * `rasterization_order_depth_attachment_access::Bool`
  * `rasterization_order_stencil_attachment_access::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT.html)

```julia
_PhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT(
    rasterization_order_color_attachment_access::Bool,
    rasterization_order_depth_attachment_access::Bool,
    rasterization_order_stencil_attachment_access::Bool;
    next
) -> Vulkan._PhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT

```
