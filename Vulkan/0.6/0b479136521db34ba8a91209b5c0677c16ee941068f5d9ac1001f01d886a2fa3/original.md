Extension: VK_EXT_image_view_min_lod

Arguments:

  * `min_lod::Float32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewMinLodCreateInfoEXT.html)

```julia
_ImageViewMinLodCreateInfoEXT(
    min_lod::Real;
    next
) -> Vulkan._ImageViewMinLodCreateInfoEXT

```
