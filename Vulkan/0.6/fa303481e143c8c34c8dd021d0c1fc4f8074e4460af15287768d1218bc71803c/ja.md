拡張: VK*KHR*acceleration_structure

引数:

  * `acceleration_structures::Vector{AccelerationStructureKHR}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetAccelerationStructureKHR.html)

```julia
_WriteDescriptorSetAccelerationStructureKHR(
    acceleration_structures::AbstractArray;
    next
) -> Vulkan._WriteDescriptorSetAccelerationStructureKHR

```
