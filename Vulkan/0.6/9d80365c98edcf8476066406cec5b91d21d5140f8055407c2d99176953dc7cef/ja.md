拡張: VK*NV*compute*shader*derivatives

引数:

  * `compute_derivative_group_quads::Bool`
  * `compute_derivative_group_linear::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceComputeShaderDerivativesFeaturesNV.html)

```julia
_PhysicalDeviceComputeShaderDerivativesFeaturesNV(
    compute_derivative_group_quads::Bool,
    compute_derivative_group_linear::Bool;
    next
) -> Vulkan._PhysicalDeviceComputeShaderDerivativesFeaturesNV

```
