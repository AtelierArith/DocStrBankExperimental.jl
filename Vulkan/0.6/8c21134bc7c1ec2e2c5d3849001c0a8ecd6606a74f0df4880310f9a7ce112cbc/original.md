Extension: VK_KHR_external_fence_fd

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`

Arguments:

  * `device::Device`
  * `import_fence_fd_info::_ImportFenceFdInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkImportFenceFdKHR.html)

```julia
_import_fence_fd_khr(
    device,
    import_fence_fd_info::Vulkan._ImportFenceFdInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
