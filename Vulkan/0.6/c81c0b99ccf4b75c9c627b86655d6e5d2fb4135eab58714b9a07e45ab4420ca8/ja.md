拡張: VK*NVX*binary_import

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::_CuModuleCreateInfoNVX`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
_create_cu_module_nvx(
    device,
    create_info::Vulkan._CuModuleCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuModuleNVX, Vulkan.VulkanError}

```
