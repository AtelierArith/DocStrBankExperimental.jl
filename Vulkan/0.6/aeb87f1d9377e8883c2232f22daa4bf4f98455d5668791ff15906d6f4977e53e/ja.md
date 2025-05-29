VkPhysicalDeviceFragmentDensityMapPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*fragment*density*map

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapPropertiesEXT.html)

```julia
struct PhysicalDeviceFragmentDensityMapPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `min_fragment_density_texel_size::Vulkan.Extent2D`
  * `max_fragment_density_texel_size::Vulkan.Extent2D`
  * `fragment_density_invocations::Bool`
