High-level wrapper for VkPipelineVertexInputStateCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputStateCreateInfo.html)

```julia
struct PipelineVertexInputStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `vertex_binding_descriptions::Vector{Vulkan.VertexInputBindingDescription}`
  * `vertex_attribute_descriptions::Vector{Vulkan.VertexInputAttributeDescription}`
