Extension: VK_NVX_binary_import

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `create_info::CuModuleCreateInfoNVX`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
create_cu_module_nvx(
    device,
    create_info::Vulkan.CuModuleCreateInfoNVX;
    allocator
) -> ResultTypes.Result{Vulkan.CuModuleNVX, Vulkan.VulkanError}

```
