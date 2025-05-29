High-level wrapper for VkPipelineDynamicStateCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDynamicStateCreateInfo.html)

```julia
struct PipelineDynamicStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `dynamic_states::Vector{Vulkan.DynamicState}`
