Arguments:

  * `device::Device`
  * `semaphore::Semaphore` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySemaphore.html)

```julia
destroy_semaphore(device, semaphore; allocator)

```
