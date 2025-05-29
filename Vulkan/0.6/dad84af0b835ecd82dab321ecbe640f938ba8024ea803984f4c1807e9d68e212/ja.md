拡張: VK*KHR*external*fence*fd

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

引数:

  * `device::Device`
  * `import_fence_fd_info::ImportFenceFdInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkImportFenceFdKHR.html)

```julia
import_fence_fd_khr(
    device,
    import_fence_fd_info::Vulkan.ImportFenceFdInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
