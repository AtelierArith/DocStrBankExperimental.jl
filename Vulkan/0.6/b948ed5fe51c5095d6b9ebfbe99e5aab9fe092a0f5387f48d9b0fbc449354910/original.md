Extension: VK_NV_present_barrier

Arguments:

  * `present_barrier::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentBarrierFeaturesNV.html)

```julia
_PhysicalDevicePresentBarrierFeaturesNV(
    present_barrier::Bool;
    next
) -> Vulkan._PhysicalDevicePresentBarrierFeaturesNV

```
