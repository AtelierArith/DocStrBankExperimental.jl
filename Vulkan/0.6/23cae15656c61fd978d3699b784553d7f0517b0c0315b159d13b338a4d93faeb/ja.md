引数:

  * `device::Device`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSemaphore.html)

```julia
Semaphore(
    device;
    allocator,
    next,
    flags
) -> Vulkan.Semaphore

```
