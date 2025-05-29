拡張: VK*NV*viewport_swizzle

引数:

  * `viewport_swizzles::Vector{ViewportSwizzleNV}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportSwizzleStateCreateInfoNV.html)

```julia
PipelineViewportSwizzleStateCreateInfoNV(
    viewport_swizzles::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineViewportSwizzleStateCreateInfoNV

```
