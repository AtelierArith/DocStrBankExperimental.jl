Arguments:

  * `device::Device`
  * `descriptor_pool::DescriptorPool` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDescriptorPool.html)

```julia
destroy_descriptor_pool(device, descriptor_pool; allocator)

```
