拡張: VK*NV*optical_flow

引数:

  * `supported_output_grid_sizes::OpticalFlowGridSizeFlagNV`
  * `supported_hint_grid_sizes::OpticalFlowGridSizeFlagNV`
  * `hint_supported::Bool`
  * `cost_supported::Bool`
  * `bidirectional_flow_supported::Bool`
  * `global_flow_supported::Bool`
  * `min_width::UInt32`
  * `min_height::UInt32`
  * `max_width::UInt32`
  * `max_height::UInt32`
  * `max_num_regions_of_interest::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceOpticalFlowPropertiesNV.html)

```julia
_PhysicalDeviceOpticalFlowPropertiesNV(
    supported_output_grid_sizes::Vulkan.OpticalFlowGridSizeFlagNV,
    supported_hint_grid_sizes::Vulkan.OpticalFlowGridSizeFlagNV,
    hint_supported::Bool,
    cost_supported::Bool,
    bidirectional_flow_supported::Bool,
    global_flow_supported::Bool,
    min_width::Integer,
    min_height::Integer,
    max_width::Integer,
    max_height::Integer,
    max_num_regions_of_interest::Integer;
    next
) -> Vulkan._PhysicalDeviceOpticalFlowPropertiesNV

```
