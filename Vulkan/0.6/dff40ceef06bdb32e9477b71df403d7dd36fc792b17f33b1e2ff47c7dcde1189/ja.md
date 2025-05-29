VkGeometryAABBNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGeometryAABBNV.html)

```julia
struct GeometryAABBNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `aabb_data::Union{Ptr{Nothing}, Vulkan.Buffer}`
  * `num_aab_bs::UInt32`
  * `stride::UInt32`
  * `offset::UInt64`
