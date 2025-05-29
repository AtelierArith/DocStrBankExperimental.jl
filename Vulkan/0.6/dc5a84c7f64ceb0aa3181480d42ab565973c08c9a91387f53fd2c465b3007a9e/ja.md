VkPhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*rasterization*order*attachment_access

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT.html)

```julia
struct PhysicalDeviceRasterizationOrderAttachmentAccessFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `rasterization_order_color_attachment_access::Bool`
  * `rasterization_order_depth_attachment_access::Bool`
  * `rasterization_order_stencil_attachment_access::Bool`
