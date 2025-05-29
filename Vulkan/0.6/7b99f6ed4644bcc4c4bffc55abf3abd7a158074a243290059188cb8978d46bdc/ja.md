VkBindAccelerationStructureMemoryInfoNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindAccelerationStructureMemoryInfoNV.html)

```julia
struct BindAccelerationStructureMemoryInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `acceleration_structure::Vulkan.AccelerationStructureNV`
  * `memory::Vulkan.DeviceMemory`
  * `memory_offset::UInt64`
  * `device_indices::Vector{UInt32}`
