返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `queue::Queue` (externsync)
  * `bind_info::Vector{BindSparseInfo}`
  * `fence::Fence`: デフォルトは `C_NULL` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueBindSparse.html)

```julia
queue_bind_sparse(
    queue,
    bind_info::AbstractArray;
    fence
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
