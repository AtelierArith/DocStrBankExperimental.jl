Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::SemaphoreCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSemaphore.html)

```julia
create_semaphore(
    device,
    create_info::Vulkan.SemaphoreCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Semaphore, Vulkan.VulkanError}

```
