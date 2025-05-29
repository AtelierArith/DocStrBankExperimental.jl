引数:

  * `device::Device`
  * `shader_module::ShaderModule` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyShaderModule.html)

```julia
_destroy_shader_module(device, shader_module; allocator)

```
