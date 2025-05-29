High-level wrapper for VkTilePropertiesQCOM.

Extension: VK_QCOM_tile_properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTilePropertiesQCOM.html)

```julia
struct TilePropertiesQCOM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `tile_size::Vulkan.Extent3D`
  * `apron_size::Vulkan.Extent2D`
  * `origin::Vulkan.Offset2D`
