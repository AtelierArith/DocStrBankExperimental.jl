VkConditionalRenderingBeginInfoEXTの高レベルラッパー。

拡張: VK*EXT*conditional_rendering

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
struct ConditionalRenderingBeginInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `flags::Vulkan.ConditionalRenderingFlagEXT`
