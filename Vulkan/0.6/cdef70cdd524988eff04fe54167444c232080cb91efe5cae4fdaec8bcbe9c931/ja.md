引数:

  * `device_mask::UInt32`
  * `device_render_areas::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupRenderPassBeginInfo.html)

```julia
_DeviceGroupRenderPassBeginInfo(
    device_mask::Integer,
    device_render_areas::AbstractArray;
    next
) -> Vulkan._DeviceGroupRenderPassBeginInfo

```
