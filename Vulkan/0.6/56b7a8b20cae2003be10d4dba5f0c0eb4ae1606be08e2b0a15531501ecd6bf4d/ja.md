拡張: VK*NV*ray_tracing

引数:

  * `acceleration_structures::Vector{AccelerationStructureNV}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetAccelerationStructureNV.html)

```julia
_WriteDescriptorSetAccelerationStructureNV(
    acceleration_structures::AbstractArray;
    next
) -> Vulkan._WriteDescriptorSetAccelerationStructureNV

```
