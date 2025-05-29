拡張機能: VK*NV*external*memory*rdma

戻りコード:

  * `SUCCESS`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

引数:

  * `device::Device`
  * `memory_get_remote_address_info::MemoryGetRemoteAddressInfoNV`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryRemoteAddressNV.html)

```julia
get_memory_remote_address_nv(
    device,
    memory_get_remote_address_info::Vulkan.MemoryGetRemoteAddressInfoNV
) -> ResultTypes.Result{Nothing, Vulkan.VulkanError}

```
