Arguments:

  * `binding_flags::Vector{DescriptorBindingFlag}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBindingFlagsCreateInfo.html)

```julia
DescriptorSetLayoutBindingFlagsCreateInfo(
    binding_flags::AbstractArray;
    next
) -> Vulkan.DescriptorSetLayoutBindingFlagsCreateInfo

```
