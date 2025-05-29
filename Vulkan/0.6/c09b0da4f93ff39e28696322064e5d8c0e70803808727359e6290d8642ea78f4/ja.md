VkVertexInputAttributeDescription2EXTの高レベルラッパー。

拡張: VK*EXT*vertex*input*dynamic_state

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputAttributeDescription2EXT.html)

```julia
struct VertexInputAttributeDescription2EXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `location::UInt32`
  * `binding::UInt32`
  * `format::Vulkan.Format`
  * `offset::UInt32`
