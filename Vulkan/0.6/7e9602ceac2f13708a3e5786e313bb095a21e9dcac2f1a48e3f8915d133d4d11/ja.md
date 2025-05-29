拡張: VK*NV*clip*space*w_scaling

引数:

  * `viewport_w_scaling_enable::Bool`
  * `next::Any`: デフォルトは `C_NULL`
  * `viewport_w_scalings::Vector{ViewportWScalingNV}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportWScalingStateCreateInfoNV.html)

```julia
PipelineViewportWScalingStateCreateInfoNV(
    viewport_w_scaling_enable::Bool;
    next,
    viewport_w_scalings
) -> Vulkan.PipelineViewportWScalingStateCreateInfoNV

```
