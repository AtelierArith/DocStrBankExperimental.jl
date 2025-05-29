Extension: VK_KHR_external_fence_fd

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `get_fd_info::_FenceGetFdInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetFenceFdKHR.html)

```julia
_get_fence_fd_khr(
    device,
    get_fd_info::Vulkan._FenceGetFdInfoKHR
)

```
