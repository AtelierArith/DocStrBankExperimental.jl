High-level wrapper for VkVertexInputBindingDescription2EXT.

Extension: VK_EXT_vertex_input_dynamic_state

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputBindingDescription2EXT.html)

```julia
struct VertexInputBindingDescription2EXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `binding::UInt32`
  * `stride::UInt32`
  * `input_rate::Vulkan.VertexInputRate`
  * `divisor::UInt32`
