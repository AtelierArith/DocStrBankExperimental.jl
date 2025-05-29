拡張: VK*KHR*workgroup*memory*explicit_layout

引数:

  * `workgroup_memory_explicit_layout::Bool`
  * `workgroup_memory_explicit_layout_scalar_block_layout::Bool`
  * `workgroup_memory_explicit_layout_8_bit_access::Bool`
  * `workgroup_memory_explicit_layout_16_bit_access::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR.html)

```julia
_PhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR(
    workgroup_memory_explicit_layout::Bool,
    workgroup_memory_explicit_layout_scalar_block_layout::Bool,
    workgroup_memory_explicit_layout_8_bit_access::Bool,
    workgroup_memory_explicit_layout_16_bit_access::Bool;
    next
) -> Vulkan._PhysicalDeviceWorkgroupMemoryExplicitLayoutFeaturesKHR

```
