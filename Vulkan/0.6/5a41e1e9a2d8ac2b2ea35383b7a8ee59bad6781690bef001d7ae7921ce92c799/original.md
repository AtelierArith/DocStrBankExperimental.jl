Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

Arguments:

  * `device::Device`
  * `create_info::_ShaderModuleCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

```julia
_create_shader_module(
    device,
    create_info::Vulkan._ShaderModuleCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.ShaderModule, Vulkan.VulkanError}

```
