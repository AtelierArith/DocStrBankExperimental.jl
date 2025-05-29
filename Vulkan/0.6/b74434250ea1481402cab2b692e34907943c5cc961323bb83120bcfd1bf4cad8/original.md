Arguments:

  * `descriptor_counts::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetVariableDescriptorCountAllocateInfo.html)

```julia
_DescriptorSetVariableDescriptorCountAllocateInfo(
    descriptor_counts::AbstractArray;
    next
) -> Vulkan._DescriptorSetVariableDescriptorCountAllocateInfo

```
