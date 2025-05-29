拡張: VK*QCOM*tile_properties

引数:

  * `tile_size::_Extent3D`
  * `apron_size::_Extent2D`
  * `origin::_Offset2D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTilePropertiesQCOM.html)

```julia
_TilePropertiesQCOM(
    tile_size::Vulkan._Extent3D,
    apron_size::Vulkan._Extent2D,
    origin::Vulkan._Offset2D;
    next
) -> Vulkan._TilePropertiesQCOM

```
