Extension: VK_QCOM_fragment_density_map_offset

Arguments:

  * `fragment_density_offsets::Vector{_Offset2D}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassFragmentDensityMapOffsetEndInfoQCOM.html)

```julia
_SubpassFragmentDensityMapOffsetEndInfoQCOM(
    fragment_density_offsets::AbstractArray;
    next
) -> Vulkan._SubpassFragmentDensityMapOffsetEndInfoQCOM

```
