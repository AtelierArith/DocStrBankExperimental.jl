拡張: VK*NVX*binary_import

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::CuModuleCreateInfoNVX`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
create_cu_module_nvx(
    device,
    create_info::Vulkan.CuModuleCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuModuleNVX, Vulkan.VulkanError}

```
