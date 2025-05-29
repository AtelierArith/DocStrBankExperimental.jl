引数:

  * `device::Device`
  * `event::Event` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyEvent.html)

```julia
_destroy_event(device, event; allocator)

```
