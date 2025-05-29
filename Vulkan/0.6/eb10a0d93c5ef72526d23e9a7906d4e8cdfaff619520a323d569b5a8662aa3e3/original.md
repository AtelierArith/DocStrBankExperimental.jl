Extension: VK_KHR_get_display_properties2

Arguments:

  * `mode::DisplayModeKHR` (externsync)
  * `plane_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneInfo2KHR.html)

```julia
_DisplayPlaneInfo2KHR(
    mode,
    plane_index::Integer;
    next
) -> Vulkan._DisplayPlaneInfo2KHR

```
