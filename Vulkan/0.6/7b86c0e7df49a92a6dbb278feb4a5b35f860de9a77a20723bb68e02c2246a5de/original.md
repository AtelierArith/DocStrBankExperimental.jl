Arguments:

  * `view_formats::Vector{Format}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageFormatListCreateInfo.html)

```julia
_ImageFormatListCreateInfo(
    view_formats::AbstractArray;
    next
) -> Vulkan._ImageFormatListCreateInfo

```
