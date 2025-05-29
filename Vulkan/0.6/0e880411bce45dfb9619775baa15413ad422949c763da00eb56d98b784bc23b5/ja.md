引数:

  * `bindings::Vector{_DescriptorSetLayoutBinding}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutCreateInfo.html)

```julia
_DescriptorSetLayoutCreateInfo(
    bindings::AbstractArray;
    next,
    flags
) -> Vulkan._DescriptorSetLayoutCreateInfo

```
