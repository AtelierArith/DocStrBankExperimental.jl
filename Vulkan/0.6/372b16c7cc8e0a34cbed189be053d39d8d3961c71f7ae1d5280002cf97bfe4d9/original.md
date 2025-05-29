High-level wrapper for VkConditionalRenderingBeginInfoEXT.

Extension: VK_EXT_conditional_rendering

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkConditionalRenderingBeginInfoEXT.html)

```julia
struct ConditionalRenderingBeginInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `flags::Vulkan.ConditionalRenderingFlagEXT`
