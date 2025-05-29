Arguments:

  * `max_sets::UInt32`
  * `pool_sizes::Vector{_DescriptorPoolSize}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorPoolCreateInfo.html)

```julia
_DescriptorPoolCreateInfo(
    max_sets::Integer,
    pool_sizes::AbstractArray;
    next,
    flags
) -> Vulkan._DescriptorPoolCreateInfo

```
