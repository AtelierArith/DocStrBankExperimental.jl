引数:

  * `device::Device`
  * `buffer_view::BufferView` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyBufferView.html)

```julia
_destroy_buffer_view(device, buffer_view; allocator)

```
