VkDescriptorAddressInfoEXTの高レベルラッパー。

拡張: VK*EXT*descriptor_buffer

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorAddressInfoEXT.html)

```julia
struct DescriptorAddressInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `address::UInt64`
  * `range::UInt64`
  * `format::Vulkan.Format`
