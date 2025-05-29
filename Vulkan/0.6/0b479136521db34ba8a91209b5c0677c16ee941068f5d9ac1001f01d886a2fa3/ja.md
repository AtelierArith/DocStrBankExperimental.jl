拡張: VK*EXT*image*view*min_lod

引数:

  * `min_lod::Float32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewMinLodCreateInfoEXT.html)

```julia
_ImageViewMinLodCreateInfoEXT(
    min_lod::Real;
    next
) -> Vulkan._ImageViewMinLodCreateInfoEXT

```
