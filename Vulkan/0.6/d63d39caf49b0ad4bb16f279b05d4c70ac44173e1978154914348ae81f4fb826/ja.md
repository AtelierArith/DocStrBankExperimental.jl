拡張: VK*NV*cooperative_matrix

引数:

  * `cooperative_matrix::Bool`
  * `cooperative_matrix_robust_buffer_access::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCooperativeMatrixFeaturesNV.html)

```julia
_PhysicalDeviceCooperativeMatrixFeaturesNV(
    cooperative_matrix::Bool,
    cooperative_matrix_robust_buffer_access::Bool;
    next
) -> Vulkan._PhysicalDeviceCooperativeMatrixFeaturesNV

```
