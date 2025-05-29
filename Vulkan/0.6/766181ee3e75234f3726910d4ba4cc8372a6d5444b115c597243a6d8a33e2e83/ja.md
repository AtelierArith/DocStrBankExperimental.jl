拡張機能: VK*EXT*display_control

引数:

  * `power_state::DisplayPowerStateEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPowerInfoEXT.html)

```julia
_DisplayPowerInfoEXT(
    power_state::Vulkan.DisplayPowerStateEXT;
    next
) -> Vulkan._DisplayPowerInfoEXT

```
