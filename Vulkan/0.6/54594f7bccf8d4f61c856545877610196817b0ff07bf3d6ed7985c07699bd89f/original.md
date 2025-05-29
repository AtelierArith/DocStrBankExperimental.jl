Arguments:

  * `view_masks::Vector{UInt32}`
  * `view_offsets::Vector{Int32}`
  * `correlation_masks::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassMultiviewCreateInfo.html)

```julia
_RenderPassMultiviewCreateInfo(
    view_masks::AbstractArray,
    view_offsets::AbstractArray,
    correlation_masks::AbstractArray;
    next
) -> Vulkan._RenderPassMultiviewCreateInfo

```
