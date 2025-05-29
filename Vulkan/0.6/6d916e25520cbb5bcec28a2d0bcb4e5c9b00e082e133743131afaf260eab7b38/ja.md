引数:

  * `device::Device`
  * `buffer_view::BufferView` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyBufferView.html)

```julia
destroy_buffer_view(device, buffer_view; allocator)

```
