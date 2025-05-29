VkDescriptorPoolCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorPoolCreateInfo.html)

```julia
struct DescriptorPoolCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DescriptorPoolCreateFlag`
  * `max_sets::UInt32`
  * `pool_sizes::Vector{Vulkan.DescriptorPoolSize}`
