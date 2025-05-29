Extension: VK_NV_ray_tracing_motion_blur

Arguments:

  * `type::AccelerationStructureMotionInstanceTypeNV`
  * `data::_AccelerationStructureMotionInstanceDataNV`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMotionInstanceNV.html)

```julia
_AccelerationStructureMotionInstanceNV(
    type::Vulkan.AccelerationStructureMotionInstanceTypeNV,
    data::Vulkan._AccelerationStructureMotionInstanceDataNV;
    flags
) -> Vulkan._AccelerationStructureMotionInstanceNV

```
