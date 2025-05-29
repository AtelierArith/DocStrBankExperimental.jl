High-level wrapper for VkMemoryGetRemoteAddressInfoNV.

Extension: VK_NV_external_memory_rdma

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetRemoteAddressInfoNV.html)

```julia
struct MemoryGetRemoteAddressInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory::Vulkan.DeviceMemory`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
