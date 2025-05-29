VkOpticalFlowSessionCreateInfoNVの高レベルラッパー。

拡張: VK*NV*optical_flow

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowSessionCreateInfoNV.html)

```julia
struct OpticalFlowSessionCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `width::UInt32`
  * `height::UInt32`
  * `image_format::Vulkan.Format`
  * `flow_vector_format::Vulkan.Format`
  * `cost_format::Vulkan.Format`
  * `output_grid_size::Vulkan.OpticalFlowGridSizeFlagNV`
  * `hint_grid_size::Vulkan.OpticalFlowGridSizeFlagNV`
  * `performance_level::Vulkan.OpticalFlowPerformanceLevelNV`
  * `flags::Vulkan.OpticalFlowSessionCreateFlagNV`
