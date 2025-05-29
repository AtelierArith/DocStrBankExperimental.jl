VkPhysicalDeviceBlendOperationAdvancedPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*blend*operation*advanced

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBlendOperationAdvancedPropertiesEXT.html)

```julia
struct PhysicalDeviceBlendOperationAdvancedPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `advanced_blend_max_color_attachments::UInt32`
  * `advanced_blend_independent_blend::Bool`
  * `advanced_blend_non_premultiplied_src_color::Bool`
  * `advanced_blend_non_premultiplied_dst_color::Bool`
  * `advanced_blend_correlated_overlap::Bool`
  * `advanced_blend_all_operations::Bool`
