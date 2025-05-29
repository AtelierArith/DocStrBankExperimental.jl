High-level wrapper for VkPipelineViewportWScalingStateCreateInfoNV.

Extension: VK_NV_clip_space_w_scaling

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportWScalingStateCreateInfoNV.html)

```julia
struct PipelineViewportWScalingStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `viewport_w_scaling_enable::Bool`
  * `viewport_w_scalings::Union{Ptr{Nothing}, Vector{Vulkan.ViewportWScalingNV}}`
