拡張: VK*KHR*display

引数:

  * `parameters::_DisplayModeParametersKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeCreateInfoKHR.html)

```julia
_DisplayModeCreateInfoKHR(
    parameters::Vulkan._DisplayModeParametersKHR;
    next,
    flags
) -> Vulkan._DisplayModeCreateInfoKHR

```
