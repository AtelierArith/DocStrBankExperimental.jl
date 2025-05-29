Arguments:

  * `device::Device`
  * `private_data_slot::PrivateDataSlot` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPrivateDataSlot.html)

```julia
destroy_private_data_slot(
    device,
    private_data_slot;
    allocator
)

```
