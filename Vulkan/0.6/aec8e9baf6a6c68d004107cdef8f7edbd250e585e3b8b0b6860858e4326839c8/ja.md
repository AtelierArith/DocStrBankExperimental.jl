拡張: VK*NV*cooperative_matrix

引数:

  * `m_size::UInt32`
  * `n_size::UInt32`
  * `k_size::UInt32`
  * `a_type::ComponentTypeNV`
  * `b_type::ComponentTypeNV`
  * `c_type::ComponentTypeNV`
  * `d_type::ComponentTypeNV`
  * `scope::ScopeNV`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCooperativeMatrixPropertiesNV.html)

```julia
_CooperativeMatrixPropertiesNV(
    m_size::Integer,
    n_size::Integer,
    k_size::Integer,
    a_type::Vulkan.ComponentTypeNV,
    b_type::Vulkan.ComponentTypeNV,
    c_type::Vulkan.ComponentTypeNV,
    d_type::Vulkan.ComponentTypeNV,
    scope::Vulkan.ScopeNV;
    next
) -> Vulkan._CooperativeMatrixPropertiesNV

```
