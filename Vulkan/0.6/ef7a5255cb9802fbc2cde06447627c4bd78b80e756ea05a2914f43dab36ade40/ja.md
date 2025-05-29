VkOpticalFlowExecuteInfoNVの高レベルラッパー。

拡張: VK*NV*optical_flow

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowExecuteInfoNV.html)

```julia
struct OpticalFlowExecuteInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.OpticalFlowExecuteFlagNV`
  * `regions::Vector{Vulkan.Rect2D}`
