引数:

  * `device::Device`
  * `render_pass::RenderPass` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyRenderPass.html)

```julia
_destroy_render_pass(device, render_pass; allocator)

```
