Arguments:

  * `size::UInt64`
  * `usage::BufferUsageFlag`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::BufferCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCreateInfo.html)

```julia
_BufferCreateInfo(
    size::Integer,
    usage::Vulkan.BufferUsageFlag,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray;
    next,
    flags
) -> Vulkan._BufferCreateInfo

```
