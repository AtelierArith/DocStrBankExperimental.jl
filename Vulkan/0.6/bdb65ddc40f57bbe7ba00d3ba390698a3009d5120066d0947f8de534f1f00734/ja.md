引数:

  * `device::Device`
  * `framebuffer::Framebuffer` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFramebuffer.html)

```julia
_destroy_framebuffer(device, framebuffer; allocator)

```
