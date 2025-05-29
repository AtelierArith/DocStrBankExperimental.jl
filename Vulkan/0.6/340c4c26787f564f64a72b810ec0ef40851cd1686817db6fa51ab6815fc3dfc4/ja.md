VkPhysicalDeviceMemoryPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryProperties.html)

```julia
struct PhysicalDeviceMemoryProperties <: Vulkan.HighLevelStruct
```

  * `memory_type_count::UInt32`
  * `memory_types::NTuple{32, Vulkan.MemoryType}`
  * `memory_heap_count::UInt32`
  * `memory_heaps::NTuple{16, Vulkan.MemoryHeap}`
