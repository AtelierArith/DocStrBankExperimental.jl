VkPipelineLayoutCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLayoutCreateInfo.html)

```julia
struct PipelineLayoutCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineLayoutCreateFlag`
  * `set_layouts::Vector{Vulkan.DescriptorSetLayout}`
  * `push_constant_ranges::Vector{Vulkan.PushConstantRange}`
