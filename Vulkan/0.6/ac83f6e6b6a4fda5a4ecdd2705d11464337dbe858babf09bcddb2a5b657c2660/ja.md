VkDescriptorSetLayoutCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutCreateInfo.html)

```julia
struct DescriptorSetLayoutCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DescriptorSetLayoutCreateFlag`
  * `bindings::Vector{Vulkan.DescriptorSetLayoutBinding}`
