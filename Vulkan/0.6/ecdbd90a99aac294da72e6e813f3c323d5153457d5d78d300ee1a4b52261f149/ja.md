返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `size::UInt64`
  * `usage::BufferUsageFlag`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::BufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBuffer.html)

```julia
_create_buffer(
    device,
    size::Integer,
    usage::Vulkan.BufferUsageFlag,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.Buffer, Vulkan.VulkanError}

```
