拡張: VK*KHR*display

引数:

  * `parameters::DisplayModeParametersKHR`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeCreateInfoKHR.html)

```julia
DisplayModeCreateInfoKHR(
    parameters::Vulkan.DisplayModeParametersKHR;
    next,
    flags
) -> Vulkan.DisplayModeCreateInfoKHR

```
