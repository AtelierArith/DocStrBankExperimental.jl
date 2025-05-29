Arguments:

  * `bindings::Vector{_DescriptorSetLayoutBinding}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutCreateInfo.html)

```julia
_DescriptorSetLayoutCreateInfo(
    bindings::AbstractArray;
    next,
    flags
) -> Vulkan._DescriptorSetLayoutCreateInfo

```
