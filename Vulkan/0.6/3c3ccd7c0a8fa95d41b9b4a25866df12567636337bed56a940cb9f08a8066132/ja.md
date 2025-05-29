返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `bind_infos::Vector{_BindBufferMemoryInfo}`

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindBufferMemory2.html)

```julia
_bind_buffer_memory_2(
    device,
    bind_infos::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
