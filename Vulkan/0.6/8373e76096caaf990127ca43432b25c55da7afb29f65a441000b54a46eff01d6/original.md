Arguments:

  * `subpass::UInt32`
  * `occlusion_query_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `render_pass::RenderPass`: defaults to `C_NULL`
  * `framebuffer::Framebuffer`: defaults to `C_NULL`
  * `query_flags::QueryControlFlag`: defaults to `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceInfo.html)

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
