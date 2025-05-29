引数:

  * `binding_flags::Vector{DescriptorBindingFlag}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBindingFlagsCreateInfo.html)

```julia
DescriptorSetLayoutBindingFlagsCreateInfo(
    binding_flags::AbstractArray;
    next
) -> Vulkan.DescriptorSetLayoutBindingFlagsCreateInfo

```
