Arguments:

  * `descriptor_counts::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetVariableDescriptorCountAllocateInfo.html)

```julia
DescriptorSetVariableDescriptorCountAllocateInfo(
    descriptor_counts::AbstractArray;
    next
) -> Vulkan.DescriptorSetVariableDescriptorCountAllocateInfo

```
