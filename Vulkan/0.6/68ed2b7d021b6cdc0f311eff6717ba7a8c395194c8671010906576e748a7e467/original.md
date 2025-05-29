Arguments:

  * `device::Device`
  * `command_pool::CommandPool` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyCommandPool.html)

```julia
destroy_command_pool(device, command_pool; allocator)

```
