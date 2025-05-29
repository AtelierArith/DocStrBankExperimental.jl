Extension: VK_NVX_binary_import

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `create_info::CuFunctionCreateInfoNVX`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
create_cu_function_nvx(
    device,
    create_info::Vulkan.CuFunctionCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuFunctionNVX, Vulkan.VulkanError}

```
