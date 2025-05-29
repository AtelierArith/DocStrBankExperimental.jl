拡張: VK*KHR*display

引数:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `parameters::DisplayModeParametersKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

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
