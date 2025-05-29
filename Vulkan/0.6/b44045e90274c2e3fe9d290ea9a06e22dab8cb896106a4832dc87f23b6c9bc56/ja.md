引数:

  * `binding_flags::Vector{DescriptorBindingFlag}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBindingFlagsCreateInfo.html)

```julia
_DescriptorSetLayoutBindingFlagsCreateInfo(
    binding_flags::AbstractArray;
    next
) -> Vulkan._DescriptorSetLayoutBindingFlagsCreateInfo

```
