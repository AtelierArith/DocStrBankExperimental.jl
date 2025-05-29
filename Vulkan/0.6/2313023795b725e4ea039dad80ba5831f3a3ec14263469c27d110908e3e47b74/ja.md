VkPhysicalDeviceDrmPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*physical*device*drm

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDrmPropertiesEXT.html)

```julia
struct PhysicalDeviceDrmPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `has_primary::Bool`
  * `has_render::Bool`
  * `primary_major::Int64`
  * `primary_minor::Int64`
  * `render_major::Int64`
  * `render_minor::Int64`
