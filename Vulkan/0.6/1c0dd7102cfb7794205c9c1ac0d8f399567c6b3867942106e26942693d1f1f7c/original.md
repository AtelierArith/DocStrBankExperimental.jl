Extension: VK_EXT_display_control

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `display::DisplayKHR`
  * `display_power_info::_DisplayPowerInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDisplayPowerControlEXT.html)

```julia
_display_power_control_ext(
    device,
    display,
    display_power_info::Vulkan._DisplayPowerInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
