Extension: VK_NV_external_memory_rdma

Arguments:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetRemoteAddressInfoNV.html)

```julia
_MemoryGetRemoteAddressInfoNV(
    memory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan._MemoryGetRemoteAddressInfoNV

```
