引数:

  * `descriptor_pool::DescriptorPool`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetAllocateInfo.html)

```julia
DescriptorSetAllocateInfo(
    descriptor_pool::Vulkan.DescriptorPool,
    set_layouts::AbstractArray;
    next
) -> Vulkan.DescriptorSetAllocateInfo

```
