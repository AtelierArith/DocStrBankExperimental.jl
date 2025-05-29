引数:

  * `device::Device`
  * `buffer::Buffer` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyBuffer.html)

```julia
destroy_buffer(device, buffer; allocator)

```
