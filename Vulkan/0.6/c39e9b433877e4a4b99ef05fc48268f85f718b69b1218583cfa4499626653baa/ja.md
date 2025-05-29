拡張: VK*KHR*external*memory*fd

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `get_fd_info::_MemoryGetFdInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMemoryFdKHR.html)

```julia
_get_memory_fd_khr(
    device,
    get_fd_info::Vulkan._MemoryGetFdInfoKHR
)

```
