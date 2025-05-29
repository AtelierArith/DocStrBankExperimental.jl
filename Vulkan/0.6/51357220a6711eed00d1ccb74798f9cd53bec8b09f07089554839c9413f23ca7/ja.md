引数:

  * `device::Device`
  * `descriptor_update_template::DescriptorUpdateTemplate` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDescriptorUpdateTemplate.html)

```julia
_destroy_descriptor_update_template(
    device,
    descriptor_update_template;
    allocator
)

```
