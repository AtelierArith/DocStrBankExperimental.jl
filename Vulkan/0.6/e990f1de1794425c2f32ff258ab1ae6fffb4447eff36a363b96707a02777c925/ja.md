引数:

  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutCreateInfo.html)

```julia
DescriptorSetLayoutCreateInfo(
    bindings::AbstractArray;
    next,
    flags
) -> Vulkan.DescriptorSetLayoutCreateInfo

```
