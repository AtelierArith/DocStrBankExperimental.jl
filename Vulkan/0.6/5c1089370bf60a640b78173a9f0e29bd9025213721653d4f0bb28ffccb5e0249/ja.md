引数:

  * `max_sets::UInt32`
  * `pool_sizes::Vector{DescriptorPoolSize}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorPoolCreateInfo.html)

```julia
DescriptorPoolCreateInfo(
    max_sets::Integer,
    pool_sizes::AbstractArray;
    next,
    flags
) -> Vulkan.DescriptorPoolCreateInfo

```
