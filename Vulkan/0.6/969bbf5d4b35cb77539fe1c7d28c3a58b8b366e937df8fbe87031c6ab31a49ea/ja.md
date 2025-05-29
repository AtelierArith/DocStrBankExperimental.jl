拡張: VK*EXT*external*memory*host

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

引数:

  * `device::Device`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Cvoid}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryHostPointerPropertiesEXT.html)

```julia
get_memory_host_pointer_properties_ext(
    device,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    host_pointer::Ptr{Nothing}
) -> ResultTypes.Result{Vulkan.MemoryHostPointerPropertiesEXT, Vulkan.VulkanError}

```
