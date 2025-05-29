VkPhysicalDeviceMeshShaderFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*mesh_shader

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMeshShaderFeaturesEXT.html)

```julia
struct PhysicalDeviceMeshShaderFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `task_shader::Bool`
  * `mesh_shader::Bool`
  * `multiview_mesh_shader::Bool`
  * `primitive_fragment_shading_rate_mesh_shader::Bool`
  * `mesh_shader_queries::Bool`
