Arguments:

  * `device::Device`
  * `bindings::Vector{_DescriptorSetLayoutBinding}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
DescriptorSetLayout(
    device,
    bindings::AbstractArray{Vulkan._DescriptorSetLayoutBinding};
    allocator,
    next,
    flags
) -> Vulkan.DescriptorSetLayout

```
