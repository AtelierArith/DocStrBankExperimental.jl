拡張機能: VK*EXT*display_control

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `display::DisplayKHR`
  * `display_event_info::_DisplayEventInfoEXT`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkRegisterDisplayEventEXT.html)

```julia
_register_display_event_ext(
    device,
    display,
    display_event_info::Vulkan._DisplayEventInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.Fence, Vulkan.VulkanError}

```
