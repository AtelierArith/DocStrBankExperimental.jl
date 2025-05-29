戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::SemaphoreCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSemaphore.html)

```julia
create_semaphore(
    device,
    create_info::Vulkan.SemaphoreCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Semaphore, Vulkan.VulkanError}

```
