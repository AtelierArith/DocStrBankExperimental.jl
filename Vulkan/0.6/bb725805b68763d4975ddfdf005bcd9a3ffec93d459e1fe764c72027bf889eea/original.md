Extension: VK_NV_external_memory_rdma

Arguments:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetRemoteAddressInfoNV.html)

```julia
MemoryGetRemoteAddressInfoNV(
    memory::Vulkan.DeviceMemory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan.MemoryGetRemoteAddressInfoNV

```
