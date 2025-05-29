High-level wrapper for VkDescriptorAddressInfoEXT.

Extension: VK_EXT_descriptor_buffer

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorAddressInfoEXT.html)

```julia
struct DescriptorAddressInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `address::UInt64`
  * `range::UInt64`
  * `format::Vulkan.Format`
