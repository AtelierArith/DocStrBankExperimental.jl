拡張: VK*NV*ray*tracing*motion_blur

引数:

  * `max_instances::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMotionInfoNV.html)

```julia
_AccelerationStructureMotionInfoNV(
    max_instances::Integer;
    next,
    flags
) -> Vulkan._AccelerationStructureMotionInfoNV

```
