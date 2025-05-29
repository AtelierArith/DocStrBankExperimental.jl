Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `queue::Queue` (externsync)
  * `submits::Vector{SubmitInfo}`
  * `fence::Fence`: defaults to `C_NULL` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueSubmit.html)

```julia
queue_submit(
    queue,
    submits::AbstractArray;
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
