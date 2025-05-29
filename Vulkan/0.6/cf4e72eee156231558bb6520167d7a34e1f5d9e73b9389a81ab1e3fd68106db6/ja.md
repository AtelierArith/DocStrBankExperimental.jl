引数:

  * `device::Device`
  * `shader_module::ShaderModule` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyShaderModule.html)

```julia
destroy_shader_module(device, shader_module; allocator)

```
