Arguments:

  * `device::Device`
  * `memory::DeviceMemory` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFreeMemory.html)

```julia
free_memory(device, memory; allocator)

```
