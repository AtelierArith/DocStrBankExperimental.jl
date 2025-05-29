拡張: VK*EXT*depth*clip*enable

引数:

  * `depth_clip_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationDepthClipStateCreateInfoEXT.html)

```julia
_PipelineRasterizationDepthClipStateCreateInfoEXT(
    depth_clip_enable::Bool;
    next,
    flags
) -> Vulkan._PipelineRasterizationDepthClipStateCreateInfoEXT

```
