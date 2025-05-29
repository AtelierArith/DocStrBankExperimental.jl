拡張: VK*QCOM*fragment*density*map_offset

引数:

  * `fragment_density_offsets::Vector{Offset2D}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassFragmentDensityMapOffsetEndInfoQCOM.html)

```julia
SubpassFragmentDensityMapOffsetEndInfoQCOM(
    fragment_density_offsets::AbstractArray;
    next
) -> Vulkan.SubpassFragmentDensityMapOffsetEndInfoQCOM

```
