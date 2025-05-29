拡張: VK*NV*ray*tracing*motion_blur

引数:

  * `max_instances::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMotionInfoNV.html)

```julia
AccelerationStructureMotionInfoNV(
    max_instances::Integer;
    next,
    flags
) -> Vulkan.AccelerationStructureMotionInfoNV

```
