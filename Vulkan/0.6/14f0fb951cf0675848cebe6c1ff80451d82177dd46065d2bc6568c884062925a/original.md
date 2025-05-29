Extension: VK_KHR_get_display_properties2

Arguments:

  * `mode::DisplayModeKHR` (externsync)
  * `plane_index::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneInfo2KHR.html)

```julia
DisplayPlaneInfo2KHR(
    mode::Vulkan.DisplayModeKHR,
    plane_index::Integer;
    next
) -> Vulkan.DisplayPlaneInfo2KHR

```
