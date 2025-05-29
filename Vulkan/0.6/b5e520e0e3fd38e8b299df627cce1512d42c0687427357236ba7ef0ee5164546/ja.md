引数:

  * `device::Device`
  * `bindings::Vector{_DescriptorSetLayoutBinding}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
DescriptorSetLayout(
    device,
    bindings::AbstractArray{Vulkan._DescriptorSetLayoutBinding};
    allocator,
    next,
    flags
) -> Vulkan.DescriptorSetLayout

```
