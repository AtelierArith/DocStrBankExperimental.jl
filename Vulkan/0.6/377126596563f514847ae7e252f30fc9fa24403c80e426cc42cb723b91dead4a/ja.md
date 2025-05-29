拡張機能: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `parameters::_DisplayModeParametersKHR`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
_create_display_mode_khr(
    physical_device,
    display,
    parameters::Vulkan._DisplayModeParametersKHR;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.DisplayModeKHR, Vulkan.VulkanError}

```
