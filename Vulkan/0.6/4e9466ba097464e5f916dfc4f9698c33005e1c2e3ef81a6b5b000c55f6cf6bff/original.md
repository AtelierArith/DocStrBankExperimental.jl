Arguments:

  * `device::Device`
  * `descriptor_set_layout::DescriptorSetLayout` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDescriptorSetLayout.html)

```julia
_destroy_descriptor_set_layout(
    device,
    descriptor_set_layout;
    allocator
)

```
