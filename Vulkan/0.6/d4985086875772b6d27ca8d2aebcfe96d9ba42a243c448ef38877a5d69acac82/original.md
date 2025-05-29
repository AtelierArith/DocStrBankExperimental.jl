Arguments:

  * `descriptor_pool::DescriptorPool`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetAllocateInfo.html)

```julia
_DescriptorSetAllocateInfo(
    descriptor_pool,
    set_layouts::AbstractArray;
    next
) -> Vulkan._DescriptorSetAllocateInfo

```
