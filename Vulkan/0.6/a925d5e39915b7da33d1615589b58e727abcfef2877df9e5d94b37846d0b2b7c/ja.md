VkDescriptorBufferBindingInfoEXTの高レベルラッパー。

拡張: VK*EXT*descriptor_buffer

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferBindingInfoEXT.html)

```julia
struct DescriptorBufferBindingInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `address::UInt64`
  * `usage::Vulkan.BufferUsageFlag`
