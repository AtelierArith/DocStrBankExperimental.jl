引数:

  * `descriptor_pool::DescriptorPool`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetAllocateInfo.html)

```julia
_DescriptorSetAllocateInfo(
    descriptor_pool,
    set_layouts::AbstractArray;
    next
) -> Vulkan._DescriptorSetAllocateInfo

```
