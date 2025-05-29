拡張: VK*KHR*acceleration_structure

引数:

  * `acceleration_structure_size::UInt64`
  * `update_scratch_size::UInt64`
  * `build_scratch_size::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildSizesInfoKHR.html)

```julia
AccelerationStructureBuildSizesInfoKHR(
    acceleration_structure_size::Integer,
    update_scratch_size::Integer,
    build_scratch_size::Integer;
    next
) -> Vulkan.AccelerationStructureBuildSizesInfoKHR

```
