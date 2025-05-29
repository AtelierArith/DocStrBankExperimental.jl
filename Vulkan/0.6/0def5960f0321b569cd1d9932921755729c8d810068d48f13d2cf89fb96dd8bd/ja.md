拡張: VK*KHR*acceleration_structure

引数:

  * `version_data::Vector{UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureVersionInfoKHR.html)

```julia
AccelerationStructureVersionInfoKHR(
    version_data::AbstractArray;
    next
) -> Vulkan.AccelerationStructureVersionInfoKHR

```
