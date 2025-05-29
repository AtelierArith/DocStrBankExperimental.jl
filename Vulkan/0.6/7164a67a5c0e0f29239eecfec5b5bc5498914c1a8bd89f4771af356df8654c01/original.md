Arguments:

  * `descriptor_pool::DescriptorPool`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetAllocateInfo.html)

```julia
DescriptorSetAllocateInfo(
    descriptor_pool::Vulkan.DescriptorPool,
    set_layouts::AbstractArray;
    next
) -> Vulkan.DescriptorSetAllocateInfo

```
