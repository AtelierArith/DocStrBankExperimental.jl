Extension: VK_EXT_display_control

Arguments:

  * `power_state::DisplayPowerStateEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPowerInfoEXT.html)

```julia
_DisplayPowerInfoEXT(
    power_state::Vulkan.DisplayPowerStateEXT;
    next
) -> Vulkan._DisplayPowerInfoEXT

```
