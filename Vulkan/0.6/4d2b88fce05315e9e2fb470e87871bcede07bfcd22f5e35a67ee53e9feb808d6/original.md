Extension: VK_NV_cooperative_matrix

Arguments:

  * `cooperative_matrix_supported_stages::ShaderStageFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCooperativeMatrixPropertiesNV.html)

```julia
_PhysicalDeviceCooperativeMatrixPropertiesNV(
    cooperative_matrix_supported_stages::Vulkan.ShaderStageFlag;
    next
) -> Vulkan._PhysicalDeviceCooperativeMatrixPropertiesNV

```
