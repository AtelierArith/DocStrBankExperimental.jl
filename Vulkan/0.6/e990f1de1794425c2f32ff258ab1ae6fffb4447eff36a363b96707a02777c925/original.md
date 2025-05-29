Arguments:

  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutCreateInfo.html)

```julia
DescriptorSetLayoutCreateInfo(
    bindings::AbstractArray;
    next,
    flags
) -> Vulkan.DescriptorSetLayoutCreateInfo

```
