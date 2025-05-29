拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `create_info::DisplayModeCreateInfoKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
create_display_mode_khr(
    physical_device,
    display,
    create_info::Vulkan.DisplayModeCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.DisplayModeKHR, Vulkan.VulkanError}

```
