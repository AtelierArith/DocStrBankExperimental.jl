戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `memory_ranges::Vector{_MappedMemoryRange}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFlushMappedMemoryRanges.html)

```julia
_flush_mapped_memory_ranges(
    device,
    memory_ranges::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
