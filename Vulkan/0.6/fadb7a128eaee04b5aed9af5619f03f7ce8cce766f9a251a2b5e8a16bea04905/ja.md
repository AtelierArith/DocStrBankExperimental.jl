拡張: VK*KHR*external*semaphore*fd

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

引数:

  * `device::Device`
  * `import_semaphore_fd_info::ImportSemaphoreFdInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkImportSemaphoreFdKHR.html)

```julia
import_semaphore_fd_khr(
    device,
    import_semaphore_fd_info::Vulkan.ImportSemaphoreFdInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
