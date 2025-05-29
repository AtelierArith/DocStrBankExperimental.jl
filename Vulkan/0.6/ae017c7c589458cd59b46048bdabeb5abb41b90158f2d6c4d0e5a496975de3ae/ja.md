VkPipelineColorBlendAdvancedStateCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*blend*operation*advanced

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendAdvancedStateCreateInfoEXT.html)

```julia
struct PipelineColorBlendAdvancedStateCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_premultiplied::Bool`
  * `dst_premultiplied::Bool`
  * `blend_overlap::Vulkan.BlendOverlapEXT`
