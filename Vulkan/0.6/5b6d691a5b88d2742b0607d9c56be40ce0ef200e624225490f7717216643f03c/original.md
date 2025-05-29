Extension: VK_NV_external_memory_rdma

Return codes:

  * `SUCCESS`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

Arguments:

  * `device::Device`
  * `memory_get_remote_address_info::MemoryGetRemoteAddressInfoNV`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryRemoteAddressNV.html)

```julia
get_memory_remote_address_nv(
    device,
    memory_get_remote_address_info::Vulkan.MemoryGetRemoteAddressInfoNV
) -> ResultTypes.Result{Nothing, Vulkan.VulkanError}

```
