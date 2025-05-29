引数:

  * `device::Device`
  * `memory::DeviceMemory` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFreeMemory.html)

```julia
_free_memory(device, memory; allocator)

```
