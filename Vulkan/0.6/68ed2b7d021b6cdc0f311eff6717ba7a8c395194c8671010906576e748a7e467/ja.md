引数:

  * `device::Device`
  * `command_pool::CommandPool` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyCommandPool.html)

```julia
destroy_command_pool(device, command_pool; allocator)

```
