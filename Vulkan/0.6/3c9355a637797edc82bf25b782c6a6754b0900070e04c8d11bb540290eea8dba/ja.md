引数:

  * `memory_barriers::Vector{_MemoryBarrier2}`
  * `buffer_memory_barriers::Vector{_BufferMemoryBarrier2}`
  * `image_memory_barriers::Vector{_ImageMemoryBarrier2}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `dependency_flags::DependencyFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDependencyInfo.html)

```julia
_DependencyInfo(
    memory_barriers::AbstractArray,
    buffer_memory_barriers::AbstractArray,
    image_memory_barriers::AbstractArray;
    next,
    dependency_flags
) -> Vulkan._DependencyInfo

```
