Extension: VK_KHR_external_semaphore_fd

Arguments:

  * `semaphore::Semaphore` (externsync)
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `fd::Int`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::SemaphoreImportFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
_ImportSemaphoreFdInfoKHR(
    semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan._ImportSemaphoreFdInfoKHR

```
