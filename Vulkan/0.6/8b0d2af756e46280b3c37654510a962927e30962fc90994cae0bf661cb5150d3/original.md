Extension: VK_KHR_display

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `parameters::_DisplayModeParametersKHR`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
DisplayModeKHR(
    physical_device,
    display,
    parameters::Vulkan._DisplayModeParametersKHR;
    allocator,
    next,
    flags
) -> Vulkan.DisplayModeKHR

```
