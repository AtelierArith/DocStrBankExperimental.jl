Extension: VK_NVX_binary_import

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuModuleNVX.html)

```julia
_create_cu_module_nvx(
    device,
    data_size::Integer,
    data::Ptr{Nothing};
    allocator,
    next
) -> ResultTypes.Result{Vulkan.CuModuleNVX, Vulkan.VulkanError}

```
