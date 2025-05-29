VkPhysicalDeviceOpticalFlowPropertiesNVの高レベルラッパー。

拡張: VK*NV*optical_flow

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceOpticalFlowPropertiesNV.html)

```julia
struct PhysicalDeviceOpticalFlowPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `supported_output_grid_sizes::Vulkan.OpticalFlowGridSizeFlagNV`
  * `supported_hint_grid_sizes::Vulkan.OpticalFlowGridSizeFlagNV`
  * `hint_supported::Bool`
  * `cost_supported::Bool`
  * `bidirectional_flow_supported::Bool`
  * `global_flow_supported::Bool`
  * `min_width::UInt32`
  * `min_height::UInt32`
  * `max_width::UInt32`
  * `max_height::UInt32`
  * `max_num_regions_of_interest::UInt32`
