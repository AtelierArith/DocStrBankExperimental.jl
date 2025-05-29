返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `queue::Queue` (externsync)
  * `submits::Vector{_SubmitInfo2}`
  * `fence::Fence`: デフォルトは `C_NULL` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueSubmit2.html)

```julia
_queue_submit_2(
    queue,
    submits::AbstractArray;
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
