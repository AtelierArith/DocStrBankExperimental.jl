拡張機能: VK*EXT*display_control

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `display::DisplayKHR`
  * `display_power_info::DisplayPowerInfoEXT`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDisplayPowerControlEXT.html)

```julia
display_power_control_ext(
    device,
    display,
    display_power_info::Vulkan.DisplayPowerInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
