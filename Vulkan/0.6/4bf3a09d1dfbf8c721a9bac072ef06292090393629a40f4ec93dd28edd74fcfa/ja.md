VkColorBlendAdvancedEXTの高レベルラッパー。

拡張: VK*EXT*extended*dynamic*state3

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkColorBlendAdvancedEXT.html)

```julia
struct ColorBlendAdvancedEXT <: Vulkan.HighLevelStruct
```

  * `advanced_blend_op::Vulkan.BlendOp`
  * `src_premultiplied::Bool`
  * `dst_premultiplied::Bool`
  * `blend_overlap::Vulkan.BlendOverlapEXT`
  * `clamp_results::Bool`
