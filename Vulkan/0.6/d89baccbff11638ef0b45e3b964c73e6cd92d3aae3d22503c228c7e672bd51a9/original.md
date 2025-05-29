Extension: VK_NV_optical_flow

Arguments:

  * `device::Device`
  * `width::UInt32`
  * `height::UInt32`
  * `image_format::Format`
  * `flow_vector_format::Format`
  * `output_grid_size::OpticalFlowGridSizeFlagNV`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `cost_format::Format`: defaults to `0`
  * `hint_grid_size::OpticalFlowGridSizeFlagNV`: defaults to `0`
  * `performance_level::OpticalFlowPerformanceLevelNV`: defaults to `0`
  * `flags::OpticalFlowSessionCreateFlagNV`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateOpticalFlowSessionNV.html)

```julia
OpticalFlowSessionNV(
    device,
    width::Integer,
    height::Integer,
    image_format::Vulkan.Format,
    flow_vector_format::Vulkan.Format,
    output_grid_size::Vulkan.OpticalFlowGridSizeFlagNV;
    allocator,
    next,
    cost_format,
    hint_grid_size,
    performance_level,
    flags
)

```
