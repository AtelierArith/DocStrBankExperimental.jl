返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `buffer::Buffer` (externsync)
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindBufferMemory.html)

```julia
bind_buffer_memory(
    device,
    buffer,
    memory,
    memory_offset::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
