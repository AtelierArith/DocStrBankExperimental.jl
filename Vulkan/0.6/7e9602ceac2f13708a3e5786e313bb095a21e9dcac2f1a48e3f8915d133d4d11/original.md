Extension: VK_NV_clip_space_w_scaling

Arguments:

  * `viewport_w_scaling_enable::Bool`
  * `next::Any`: defaults to `C_NULL`
  * `viewport_w_scalings::Vector{ViewportWScalingNV}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportWScalingStateCreateInfoNV.html)

```julia
PipelineViewportWScalingStateCreateInfoNV(
    viewport_w_scaling_enable::Bool;
    next,
    viewport_w_scalings
) -> Vulkan.PipelineViewportWScalingStateCreateInfoNV

```
