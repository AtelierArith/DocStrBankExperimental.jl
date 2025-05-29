VkGeometryNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryNV.html)

```julia
struct GeometryNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `geometry_type::Vulkan.GeometryTypeKHR`
  * `geometry::Vulkan.GeometryDataNV`
  * `flags::Vulkan.GeometryFlagKHR`
