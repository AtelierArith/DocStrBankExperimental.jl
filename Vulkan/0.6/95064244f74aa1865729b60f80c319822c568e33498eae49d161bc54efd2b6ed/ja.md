拡張: VK*KHR*external*semaphore*fd

引数:

  * `semaphore::Semaphore`
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
_SemaphoreGetFdInfoKHR(
    semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next
) -> Vulkan._SemaphoreGetFdInfoKHR

```
