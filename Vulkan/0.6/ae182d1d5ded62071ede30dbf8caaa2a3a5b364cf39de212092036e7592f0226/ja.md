拡張: VK*KHR*external*memory*fd

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

引数:

  * `device::Device`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `fd::Int`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryFdPropertiesKHR.html)

```julia
get_memory_fd_properties_khr(
    device,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    fd::Integer
) -> ResultTypes.Result{Vulkan.MemoryFdPropertiesKHR, Vulkan.VulkanError}

```
