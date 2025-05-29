Extension: VK_NV_ray_tracing_motion_blur

Arguments:

  * `max_instances::UInt32`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMotionInfoNV.html)

```julia
AccelerationStructureMotionInfoNV(
    max_instances::Integer;
    next,
    flags
) -> Vulkan.AccelerationStructureMotionInfoNV

```
