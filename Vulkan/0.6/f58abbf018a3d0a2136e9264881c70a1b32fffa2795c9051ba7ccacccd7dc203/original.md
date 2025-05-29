Arguments:

  * `device::Device`
  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
DescriptorSetLayout(
    device,
    bindings::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.DescriptorSetLayout

```
