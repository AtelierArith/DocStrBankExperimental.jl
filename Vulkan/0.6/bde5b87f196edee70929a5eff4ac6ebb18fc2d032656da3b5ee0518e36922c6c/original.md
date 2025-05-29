Extension: VK_NV_viewport_swizzle

Arguments:

  * `viewport_swizzles::Vector{_ViewportSwizzleNV}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportSwizzleStateCreateInfoNV.html)

```julia
_PipelineViewportSwizzleStateCreateInfoNV(
    viewport_swizzles::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineViewportSwizzleStateCreateInfoNV

```
