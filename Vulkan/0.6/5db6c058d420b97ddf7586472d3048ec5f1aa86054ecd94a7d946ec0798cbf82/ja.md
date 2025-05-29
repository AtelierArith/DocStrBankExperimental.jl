VkCooperativeMatrixPropertiesNVの高レベルラッパー。

拡張: VK*NV*cooperative_matrix

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCooperativeMatrixPropertiesNV.html)

```julia
struct CooperativeMatrixPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `m_size::UInt32`
  * `n_size::UInt32`
  * `k_size::UInt32`
  * `a_type::Vulkan.ComponentTypeNV`
  * `b_type::Vulkan.ComponentTypeNV`
  * `c_type::Vulkan.ComponentTypeNV`
  * `d_type::Vulkan.ComponentTypeNV`
  * `scope::Vulkan.ScopeNV`
