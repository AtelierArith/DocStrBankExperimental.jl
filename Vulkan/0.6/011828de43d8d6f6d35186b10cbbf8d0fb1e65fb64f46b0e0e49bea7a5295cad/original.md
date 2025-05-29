Extension: VK_EXT_depth_clip_enable

Arguments:

  * `depth_clip_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationDepthClipStateCreateInfoEXT.html)

```julia
_PipelineRasterizationDepthClipStateCreateInfoEXT(
    depth_clip_enable::Bool;
    next,
    flags
) -> Vulkan._PipelineRasterizationDepthClipStateCreateInfoEXT

```
