引数:

  * `device::Device`
  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
DescriptorSetLayout(
    device,
    bindings::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.DescriptorSetLayout

```
