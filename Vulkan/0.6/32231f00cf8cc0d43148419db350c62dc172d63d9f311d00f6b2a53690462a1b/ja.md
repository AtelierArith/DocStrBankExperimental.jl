VkMemoryAllocateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateInfo.html)

```julia
struct MemoryAllocateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
