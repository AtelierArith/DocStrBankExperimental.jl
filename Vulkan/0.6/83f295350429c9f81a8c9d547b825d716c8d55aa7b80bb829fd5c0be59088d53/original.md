Extension: VK_KHR_display

Arguments:

  * `parameters::_DisplayModeParametersKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeCreateInfoKHR.html)

```julia
_DisplayModeCreateInfoKHR(
    parameters::Vulkan._DisplayModeParametersKHR;
    next,
    flags
) -> Vulkan._DisplayModeCreateInfoKHR

```
