拡張: VK*EXT*depth*clip*enable

引数:

  * `depth_clip_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthClipEnableFeaturesEXT.html)

```julia
_PhysicalDeviceDepthClipEnableFeaturesEXT(
    depth_clip_enable::Bool;
    next
) -> Vulkan._PhysicalDeviceDepthClipEnableFeaturesEXT

```
