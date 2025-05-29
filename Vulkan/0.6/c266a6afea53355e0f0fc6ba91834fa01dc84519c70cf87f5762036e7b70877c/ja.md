VkBufferViewCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferViewCreateInfo.html)

```julia
struct BufferViewCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `buffer::Vulkan.Buffer`
  * `format::Vulkan.Format`
  * `offset::UInt64`
  * `range::UInt64`
