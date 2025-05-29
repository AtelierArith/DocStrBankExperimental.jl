Extension: VK_EXT_depth_clip_enable

Arguments:

  * `depth_clip_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthClipEnableFeaturesEXT.html)

```julia
_PhysicalDeviceDepthClipEnableFeaturesEXT(
    depth_clip_enable::Bool;
    next
) -> Vulkan._PhysicalDeviceDepthClipEnableFeaturesEXT

```
