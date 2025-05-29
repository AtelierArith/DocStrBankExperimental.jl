拡張: VK*KHR*external*semaphore*fd

引数:

  * `semaphore::Semaphore` (externsync)
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `fd::Int`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::SemaphoreImportFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
_ImportSemaphoreFdInfoKHR(
    semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan._ImportSemaphoreFdInfoKHR

```
