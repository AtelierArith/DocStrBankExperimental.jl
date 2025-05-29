拡張: VK*KHR*external*semaphore*fd

引数:

  * `semaphore::Semaphore`
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
SemaphoreGetFdInfoKHR(
    semaphore::Vulkan.Semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next
) -> Vulkan.SemaphoreGetFdInfoKHR

```
