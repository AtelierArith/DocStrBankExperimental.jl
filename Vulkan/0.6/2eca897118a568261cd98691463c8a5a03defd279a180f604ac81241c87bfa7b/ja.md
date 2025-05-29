戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `queue::Queue` (externsync)
  * `submits::Vector{_SubmitInfo}`
  * `fence::Fence`: デフォルトは `C_NULL` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueSubmit.html)

```julia
_queue_submit(
    queue,
    submits::AbstractArray;
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
