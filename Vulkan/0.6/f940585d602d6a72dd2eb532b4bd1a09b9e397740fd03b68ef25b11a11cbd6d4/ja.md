拡張機能: VK*NV*optical_flow

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `width::UInt32`
  * `height::UInt32`
  * `image_format::Format`
  * `flow_vector_format::Format`
  * `output_grid_size::OpticalFlowGridSizeFlagNV`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `cost_format::Format`: デフォルトは `0`
  * `hint_grid_size::OpticalFlowGridSizeFlagNV`: デフォルトは `0`
  * `performance_level::OpticalFlowPerformanceLevelNV`: デフォルトは `0`
  * `flags::OpticalFlowSessionCreateFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateOpticalFlowSessionNV.html)

```julia
_create_optical_flow_session_nv(
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
