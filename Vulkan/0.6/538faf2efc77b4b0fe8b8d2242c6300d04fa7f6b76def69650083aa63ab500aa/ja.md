拡張: VK*EXT*depth*clip*control

引数:

  * `depth_clip_control::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthClipControlFeaturesEXT.html)

```julia
_PhysicalDeviceDepthClipControlFeaturesEXT(
    depth_clip_control::Bool;
    next
) -> Vulkan._PhysicalDeviceDepthClipControlFeaturesEXT

```
