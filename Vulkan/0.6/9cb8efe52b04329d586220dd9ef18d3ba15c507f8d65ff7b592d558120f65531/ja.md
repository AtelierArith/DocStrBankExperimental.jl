引数:

  * `device::Device`
  * `size::UInt64`
  * `usage::BufferUsageFlag`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::BufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBuffer.html)

```julia
Buffer(
    device,
    size::Integer,
    usage::Vulkan.BufferUsageFlag,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.Buffer

```
