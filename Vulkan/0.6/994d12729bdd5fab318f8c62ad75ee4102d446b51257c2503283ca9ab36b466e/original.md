Extension: VK_KHR_display

Arguments:

  * `parameters::DisplayModeParametersKHR`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeCreateInfoKHR.html)

```julia
DisplayModeCreateInfoKHR(
    parameters::Vulkan.DisplayModeParametersKHR;
    next,
    flags
) -> Vulkan.DisplayModeCreateInfoKHR

```
