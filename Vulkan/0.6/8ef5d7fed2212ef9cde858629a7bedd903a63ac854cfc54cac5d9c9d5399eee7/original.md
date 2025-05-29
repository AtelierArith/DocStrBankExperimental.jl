Extension: VK_NVX_binary_import

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `_module::CuModuleNVX`
  * `name::String`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCuFunctionNVX.html)

```julia
_create_cu_function_nvx(
    device,
    _module,
    name::AbstractString;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.CuFunctionNVX, Vulkan.VulkanError}

```
