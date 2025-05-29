Extension: VK_KHR_display

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `parameters::DisplayModeParametersKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
DisplayModeKHR(
    physical_device,
    display,
    parameters::Vulkan.DisplayModeParametersKHR;
    allocator,
    next,
    flags
) -> Vulkan.DisplayModeKHR

```
