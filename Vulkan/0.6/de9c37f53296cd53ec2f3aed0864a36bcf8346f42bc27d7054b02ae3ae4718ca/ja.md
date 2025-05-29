拡張: VK*NVX*binary_import

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `create_info::CuFunctionCreateInfoNVX`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
create_cu_function_nvx(
    device,
    create_info::Vulkan.CuFunctionCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuFunctionNVX, Vulkan.VulkanError}

```
