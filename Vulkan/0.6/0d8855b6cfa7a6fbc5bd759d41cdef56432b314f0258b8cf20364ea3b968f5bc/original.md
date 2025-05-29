Extension: VK_KHR_external_semaphore_fd

Arguments:

  * `semaphore::Semaphore`
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
SemaphoreGetFdInfoKHR(
    semaphore::Vulkan.Semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next
) -> Vulkan.SemaphoreGetFdInfoKHR

```
