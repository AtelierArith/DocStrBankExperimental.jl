Arguments:

  * `max_sets::UInt32`
  * `pool_sizes::Vector{DescriptorPoolSize}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorPoolCreateInfo.html)

```julia
DescriptorPoolCreateInfo(
    max_sets::Integer,
    pool_sizes::AbstractArray;
    next,
    flags
) -> Vulkan.DescriptorPoolCreateInfo

```
