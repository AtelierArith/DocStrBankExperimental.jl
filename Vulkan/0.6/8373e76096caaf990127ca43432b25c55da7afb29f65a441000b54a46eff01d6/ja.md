引数:

  * `subpass::UInt32`
  * `occlusion_query_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `render_pass::RenderPass`: デフォルトは `C_NULL`
  * `framebuffer::Framebuffer`: デフォルトは `C_NULL`
  * `query_flags::QueryControlFlag`: デフォルトは `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceInfo.html)

```julia
_CommandBufferInheritanceInfo(
    subpass::Integer,
    occlusion_query_enable::Bool;
    next,
    render_pass,
    framebuffer,
    query_flags,
    pipeline_statistics
) -> Vulkan._CommandBufferInheritanceInfo

```
