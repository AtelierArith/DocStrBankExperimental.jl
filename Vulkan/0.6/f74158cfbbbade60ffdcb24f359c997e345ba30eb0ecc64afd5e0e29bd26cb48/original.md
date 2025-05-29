High-level wrapper for VkDescriptorBufferInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferInfo.html)

```julia
struct DescriptorBufferInfo <: Vulkan.HighLevelStruct
```

  * `buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `offset::UInt64`
  * `range::UInt64`
