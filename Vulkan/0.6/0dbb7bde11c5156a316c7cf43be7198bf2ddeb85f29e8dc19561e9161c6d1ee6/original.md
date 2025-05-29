Arguments:

  * `device_mask::UInt32`
  * `device_render_areas::Vector{Rect2D}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupRenderPassBeginInfo.html)

```julia
DeviceGroupRenderPassBeginInfo(
    device_mask::Integer,
    device_render_areas::AbstractArray;
    next
) -> Vulkan.DeviceGroupRenderPassBeginInfo

```
