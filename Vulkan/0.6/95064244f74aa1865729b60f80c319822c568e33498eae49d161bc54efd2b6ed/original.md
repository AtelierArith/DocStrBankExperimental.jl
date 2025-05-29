Extension: VK_KHR_external_semaphore_fd

Arguments:

  * `semaphore::Semaphore`
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
_SemaphoreGetFdInfoKHR(
    semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next
) -> Vulkan._SemaphoreGetFdInfoKHR

```
