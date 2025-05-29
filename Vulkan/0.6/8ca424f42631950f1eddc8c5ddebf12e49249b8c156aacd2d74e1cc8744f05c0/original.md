Extension: VK_KHR_external_semaphore_fd

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `get_fd_info::_SemaphoreGetFdInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSemaphoreFdKHR.html)

```julia
_get_semaphore_fd_khr(
    device,
    get_fd_info::Vulkan._SemaphoreGetFdInfoKHR
)

```
