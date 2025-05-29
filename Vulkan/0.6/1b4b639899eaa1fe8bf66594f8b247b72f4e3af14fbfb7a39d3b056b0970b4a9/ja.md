引数:

  * `queue_family_index::UInt32`
  * `queue_priorities::Vector{Float32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DeviceQueueCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueCreateInfo.html)

```julia
_DeviceQueueCreateInfo(
    queue_family_index::Integer,
    queue_priorities::AbstractArray;
    next,
    flags
) -> Vulkan._DeviceQueueCreateInfo

```
