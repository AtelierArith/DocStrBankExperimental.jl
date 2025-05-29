Extension: VK_EXT_external_memory_host

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

Arguments:

  * `device::Device`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Cvoid}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryHostPointerPropertiesEXT.html)

```julia
_get_memory_host_pointer_properties_ext(
    device,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    host_pointer::Ptr{Nothing}
) -> ResultTypes.Result{Vulkan._MemoryHostPointerPropertiesEXT, Vulkan.VulkanError}

```
