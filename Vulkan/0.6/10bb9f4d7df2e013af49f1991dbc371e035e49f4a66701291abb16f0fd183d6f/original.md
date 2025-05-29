Extension: VK_NV_copy_memory_indirect

Arguments:

  * `indirect_copy::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCopyMemoryIndirectFeaturesNV.html)

```julia
_PhysicalDeviceCopyMemoryIndirectFeaturesNV(
    indirect_copy::Bool;
    next
) -> Vulkan._PhysicalDeviceCopyMemoryIndirectFeaturesNV

```
