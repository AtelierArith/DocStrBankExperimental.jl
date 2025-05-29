Extension: VK_KHR_external_memory_fd

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `get_fd_info::_MemoryGetFdInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryFdKHR.html)

```julia
_get_memory_fd_khr(
    device,
    get_fd_info::Vulkan._MemoryGetFdInfoKHR
)

```
