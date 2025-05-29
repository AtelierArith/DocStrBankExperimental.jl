引数:

  * `device::Device`
  * `semaphore::Semaphore` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySemaphore.html)

```julia
_destroy_semaphore(device, semaphore; allocator)

```
