VkDescriptorGetInfoEXTの高レベルラッパー。

拡張: VK*EXT*descriptor_buffer

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorGetInfoEXT.html)

```julia
struct DescriptorGetInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.DescriptorType`
  * `data::Vulkan.DescriptorDataEXT`
