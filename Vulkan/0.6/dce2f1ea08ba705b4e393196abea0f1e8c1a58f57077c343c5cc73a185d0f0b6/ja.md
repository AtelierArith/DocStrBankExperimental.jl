拡張: VK*QCOM*tile_properties

引数:

  * `tile_size::Extent3D`
  * `apron_size::Extent2D`
  * `origin::Offset2D`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTilePropertiesQCOM.html)

```julia
TilePropertiesQCOM(
    tile_size::Vulkan.Extent3D,
    apron_size::Vulkan.Extent2D,
    origin::Vulkan.Offset2D;
    next
) -> Vulkan.TilePropertiesQCOM

```
