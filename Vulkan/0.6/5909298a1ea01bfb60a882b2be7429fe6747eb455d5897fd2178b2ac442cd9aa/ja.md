VkDescriptorSetAllocateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetAllocateInfo.html)

```julia
struct DescriptorSetAllocateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `descriptor_pool::Vulkan.DescriptorPool`
  * `set_layouts::Vector{Vulkan.DescriptorSetLayout}`
