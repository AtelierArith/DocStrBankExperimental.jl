VkMappedMemoryRangeの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMappedMemoryRange.html)

```julia
struct MappedMemoryRange <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory::Vulkan.DeviceMemory`
  * `offset::UInt64`
  * `size::UInt64`
