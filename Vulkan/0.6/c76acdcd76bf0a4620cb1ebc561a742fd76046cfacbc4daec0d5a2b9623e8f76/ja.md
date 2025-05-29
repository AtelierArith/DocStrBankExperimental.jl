VkSparseMemoryBindの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseMemoryBind.html)

```julia
struct SparseMemoryBind <: Vulkan.HighLevelStruct
```

  * `resource_offset::UInt64`
  * `size::UInt64`
  * `memory::Union{Ptr{Nothing}, Vulkan.DeviceMemory}`
  * `memory_offset::UInt64`
  * `flags::Vulkan.SparseMemoryBindFlag`
