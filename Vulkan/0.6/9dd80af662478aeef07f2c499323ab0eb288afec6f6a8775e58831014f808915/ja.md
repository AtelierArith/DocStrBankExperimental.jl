戻り値:

  * `SUCCESS`
  * `TIMEOUT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `device::Device`
  * `fences::Vector{Fence}`
  * `wait_all::Bool`
  * `timeout::UInt64`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWaitForFences.html)

```julia
wait_for_fences(
    device,
    fences::AbstractArray,
    wait_all::Bool,
    timeout::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
