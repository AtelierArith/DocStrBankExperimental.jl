拡張: VK*NV*external*memory*rdma

引数:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetRemoteAddressInfoNV.html)

```julia
MemoryGetRemoteAddressInfoNV(
    memory::Vulkan.DeviceMemory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan.MemoryGetRemoteAddressInfoNV

```
