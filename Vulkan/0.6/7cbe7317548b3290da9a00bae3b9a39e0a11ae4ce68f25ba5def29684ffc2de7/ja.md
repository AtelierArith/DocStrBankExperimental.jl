引数:

  * `memory_barriers::Vector{MemoryBarrier2}`
  * `buffer_memory_barriers::Vector{BufferMemoryBarrier2}`
  * `image_memory_barriers::Vector{ImageMemoryBarrier2}`
  * `next::Any`: デフォルトは `C_NULL`
  * `dependency_flags::DependencyFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDependencyInfo.html)

```julia
DependencyInfo(
    memory_barriers::AbstractArray,
    buffer_memory_barriers::AbstractArray,
    image_memory_barriers::AbstractArray;
    next,
    dependency_flags
) -> Vulkan.DependencyInfo

```
