返却コード:

  * `SUCCESS`
  * `NOT_READY`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `device::Device`
  * `fence::Fence`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetFenceStatus.html)

```julia
_get_fence_status(
    device,
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
