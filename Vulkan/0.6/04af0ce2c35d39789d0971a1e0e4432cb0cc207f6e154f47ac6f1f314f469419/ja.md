VkBindBufferMemoryInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryInfo.html)

```julia
struct BindBufferMemoryInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `buffer::Vulkan.Buffer`
  * `memory::Vulkan.DeviceMemory`
  * `memory_offset::UInt64`
