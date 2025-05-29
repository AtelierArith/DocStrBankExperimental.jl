拡張: VK*NVX*binary_import

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::_CuFunctionCreateInfoNVX`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
_create_cu_function_nvx(
    device,
    create_info::Vulkan._CuFunctionCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuFunctionNVX, Vulkan.VulkanError}

```
