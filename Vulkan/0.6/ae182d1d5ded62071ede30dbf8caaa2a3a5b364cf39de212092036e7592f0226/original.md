Extension: VK_KHR_external_memory_fd

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

Arguments:

  * `device::Device`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `fd::Int`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryFdPropertiesKHR.html)

```julia
get_memory_fd_properties_khr(
    device,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    fd::Integer
) -> ResultTypes.Result{Vulkan.MemoryFdPropertiesKHR, Vulkan.VulkanError}

```
