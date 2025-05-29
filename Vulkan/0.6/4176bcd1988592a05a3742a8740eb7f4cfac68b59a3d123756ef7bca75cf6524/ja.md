VkPhysicalDeviceFragmentDensityMap2PropertiesEXTの高レベルラッパー。

拡張: VK*EXT*fragment*density*map2

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMap2PropertiesEXT.html)

```julia
struct PhysicalDeviceFragmentDensityMap2PropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `subsampled_loads::Bool`
  * `subsampled_coarse_reconstruction_early_access::Bool`
  * `max_subsampled_array_layers::UInt32`
  * `max_descriptor_set_subsampled_samplers::UInt32`
