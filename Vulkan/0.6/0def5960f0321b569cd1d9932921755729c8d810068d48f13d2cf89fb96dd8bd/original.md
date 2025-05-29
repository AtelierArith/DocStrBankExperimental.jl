Extension: VK_KHR_acceleration_structure

Arguments:

  * `version_data::Vector{UInt8}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureVersionInfoKHR.html)

```julia
AccelerationStructureVersionInfoKHR(
    version_data::AbstractArray;
    next
) -> Vulkan.AccelerationStructureVersionInfoKHR

```
