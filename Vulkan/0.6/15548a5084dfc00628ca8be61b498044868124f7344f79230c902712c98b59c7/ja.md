VkDescriptorUpdateTemplateEntryの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorUpdateTemplateEntry.html)

```julia
struct DescriptorUpdateTemplateEntry <: Vulkan.HighLevelStruct
```

  * `dst_binding::UInt32`
  * `dst_array_element::UInt32`
  * `descriptor_count::UInt32`
  * `descriptor_type::Vulkan.DescriptorType`
  * `offset::UInt64`
  * `stride::UInt64`
