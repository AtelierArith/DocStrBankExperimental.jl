VkCopyDescriptorSetの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyDescriptorSet.html)

```julia
struct CopyDescriptorSet <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_set::Vulkan.DescriptorSet`
  * `src_binding::UInt32`
  * `src_array_element::UInt32`
  * `dst_set::Vulkan.DescriptorSet`
  * `dst_binding::UInt32`
  * `dst_array_element::UInt32`
  * `descriptor_count::UInt32`
