拡張: VK*KHR*external*semaphore*fd

引数:

  * `semaphore::Semaphore` (externsync)
  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `fd::Int`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::SemaphoreImportFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
ImportSemaphoreFdInfoKHR(
    semaphore::Vulkan.Semaphore,
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag,
    fd::Integer;
    next,
    flags
) -> Vulkan.ImportSemaphoreFdInfoKHR

```
