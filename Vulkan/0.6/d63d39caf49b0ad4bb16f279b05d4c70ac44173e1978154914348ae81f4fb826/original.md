Extension: VK_NV_cooperative_matrix

Arguments:

  * `cooperative_matrix::Bool`
  * `cooperative_matrix_robust_buffer_access::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCooperativeMatrixFeaturesNV.html)

```julia
_PhysicalDeviceCooperativeMatrixFeaturesNV(
    cooperative_matrix::Bool,
    cooperative_matrix_robust_buffer_access::Bool;
    next
) -> Vulkan._PhysicalDeviceCooperativeMatrixFeaturesNV

```
