Return codes:

  * `SUCCESS`
  * `NOT_READY`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `device::Device`
  * `fence::Fence`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetFenceStatus.html)

```julia
get_fence_status(
    device,
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
