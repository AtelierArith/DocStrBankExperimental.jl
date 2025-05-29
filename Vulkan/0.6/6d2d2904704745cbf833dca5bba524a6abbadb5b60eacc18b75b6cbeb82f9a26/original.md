Extension: VK_NV_viewport_swizzle

Arguments:

  * `viewport_swizzles::Vector{ViewportSwizzleNV}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportSwizzleStateCreateInfoNV.html)

```julia
PipelineViewportSwizzleStateCreateInfoNV(
    viewport_swizzles::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineViewportSwizzleStateCreateInfoNV

```
