High-level wrapper for VkOpticalFlowExecuteInfoNV.

Extension: VK_NV_optical_flow

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowExecuteInfoNV.html)

```julia
struct OpticalFlowExecuteInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.OpticalFlowExecuteFlagNV`
  * `regions::Vector{Vulkan.Rect2D}`
