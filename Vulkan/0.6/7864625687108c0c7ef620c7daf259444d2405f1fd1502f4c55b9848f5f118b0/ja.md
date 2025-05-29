戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::QueryPoolCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
create_query_pool(
    device,
    create_info::Vulkan.QueryPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.QueryPool, Vulkan.VulkanError}

```
