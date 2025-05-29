戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

引数:

  * `device::Device`
  * `create_info::_ShaderModuleCreateInfo`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

```julia
_create_shader_module(
    device,
    create_info::Vulkan._ShaderModuleCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.ShaderModule, Vulkan.VulkanError}

```
