拡張: VK*KHR*xcb_surface

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `connection::Ptr{xcb_connection_t}`
  * `window::xcb_window_t`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateXcbSurfaceKHR.html)

```julia
_create_xcb_surface_khr(
    instance,
    connection::Ptr{Nothing},
    window::UInt32;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
