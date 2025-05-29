Arguments:

  * `binding_flags::Vector{DescriptorBindingFlag}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBindingFlagsCreateInfo.html)

```julia
_DescriptorSetLayoutBindingFlagsCreateInfo(
    binding_flags::AbstractArray;
    next
) -> Vulkan._DescriptorSetLayoutBindingFlagsCreateInfo

```
