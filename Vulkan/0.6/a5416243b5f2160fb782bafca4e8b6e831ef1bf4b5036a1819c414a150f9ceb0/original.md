Extension: VK_KHR_workgroup_memory_explicit_layout

Arguments:

  * `workgroup_memory_explicit_layout::Bool`
  * `workgroup_memory_explicit_layout_scalar_block_layout::Bool`
  * `workgroup_memory_explicit_layout_8_bit_access::Bool`
  * `workgroup_memory_explicit_layout_16_bit_access::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR.html)

```julia
PhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR(
    workgroup_memory_explicit_layout::Bool,
    workgroup_memory_explicit_layout_scalar_block_layout::Bool,
    workgroup_memory_explicit_layout_8_bit_access::Bool,
    workgroup_memory_explicit_layout_16_bit_access::Bool;
    next
) -> Vulkan.PhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR

```
