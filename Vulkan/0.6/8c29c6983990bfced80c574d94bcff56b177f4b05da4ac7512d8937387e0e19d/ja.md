引数:

  * `device::Device`
  * `framebuffer::Framebuffer` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFramebuffer.html)

```julia
destroy_framebuffer(device, framebuffer; allocator)

```
