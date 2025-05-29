引数:

  * `size::UInt64`
  * `usage::BufferUsageFlag`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::BufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCreateInfo.html)

```julia
BufferCreateInfo(
    size::Integer,
    usage::Vulkan.BufferUsageFlag,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray;
    next,
    flags
) -> Vulkan.BufferCreateInfo

```
