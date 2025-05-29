戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_MEMORY_MAP_FAILED`

引数:

  * `device::Device`
  * `memory::DeviceMemory` (externsync)
  * `offset::UInt64`
  * `size::UInt64`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkMapMemory.html)

```julia
map_memory(
    device,
    memory,
    offset::Integer,
    size::Integer;
    flags
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
