VkPipelineViewportWScalingStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*clip*space*w_scaling

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportWScalingStateCreateInfoNV.html)

```julia
struct PipelineViewportWScalingStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `viewport_w_scaling_enable::Bool`
  * `viewport_w_scalings::Union{Ptr{Nothing}, Vector{Vulkan.ViewportWScalingNV}}`
