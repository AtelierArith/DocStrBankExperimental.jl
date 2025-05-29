Extension: VK_NV_cooperative_matrix

Arguments:

  * `m_size::UInt32`
  * `n_size::UInt32`
  * `k_size::UInt32`
  * `a_type::ComponentTypeNV`
  * `b_type::ComponentTypeNV`
  * `c_type::ComponentTypeNV`
  * `d_type::ComponentTypeNV`
  * `scope::ScopeNV`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCooperativeMatrixPropertiesNV.html)

```julia
CooperativeMatrixPropertiesNV(
    m_size::Integer,
    n_size::Integer,
    k_size::Integer,
    a_type::Vulkan.ComponentTypeNV,
    b_type::Vulkan.ComponentTypeNV,
    c_type::Vulkan.ComponentTypeNV,
    d_type::Vulkan.ComponentTypeNV,
    scope::Vulkan.ScopeNV;
    next
) -> Vulkan.CooperativeMatrixPropertiesNV

```
