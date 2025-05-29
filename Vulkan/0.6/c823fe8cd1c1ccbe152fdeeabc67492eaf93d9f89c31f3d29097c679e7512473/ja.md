引数:

  * `memory_type_count::UInt32`
  * `memory_types::NTuple{Int(VK_MAX_MEMORY_TYPES), _MemoryType}`
  * `memory_heap_count::UInt32`
  * `memory_heaps::NTuple{Int(VK_MAX_MEMORY_HEAPS), _MemoryHeap}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryProperties.html)

```julia
_PhysicalDeviceMemoryProperties(
    memory_type_count::Integer,
    memory_types::NTuple{32, Vulkan._MemoryType},
    memory_heap_count::Integer,
    memory_heaps::NTuple{16, Vulkan._MemoryHeap}
)

```
