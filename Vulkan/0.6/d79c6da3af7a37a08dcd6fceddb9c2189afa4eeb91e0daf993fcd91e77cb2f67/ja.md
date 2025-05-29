拡張: VK*KHR*external*semaphore*fd

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `get_fd_info::SemaphoreGetFdInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSemaphoreFdKHR.html)

```julia
get_semaphore_fd_khr(
    device,
    get_fd_info::Vulkan.SemaphoreGetFdInfoKHR
)

```
