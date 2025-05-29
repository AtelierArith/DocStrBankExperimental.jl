引数:

  * `device::Device`
  * `event::Event` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyEvent.html)

```julia
destroy_event(device, event; allocator)

```
