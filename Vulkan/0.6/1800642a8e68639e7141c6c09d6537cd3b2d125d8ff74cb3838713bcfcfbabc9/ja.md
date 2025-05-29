戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `image::Image` (externsync)
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindImageMemory.html)

```julia
_bind_image_memory(
    device,
    image,
    memory,
    memory_offset::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
