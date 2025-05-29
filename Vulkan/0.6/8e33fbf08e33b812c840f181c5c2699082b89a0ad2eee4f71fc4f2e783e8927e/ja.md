引数:

  * `max_sets::UInt32`
  * `pool_sizes::Vector{_DescriptorPoolSize}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorPoolCreateInfo.html)

```julia
_DescriptorPoolCreateInfo(
    max_sets::Integer,
    pool_sizes::AbstractArray;
    next,
    flags
) -> Vulkan._DescriptorPoolCreateInfo

```
