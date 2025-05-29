VkPhysicalDeviceMultiviewFeaturesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMultiviewFeatures.html)

```julia
struct PhysicalDeviceMultiviewFeatures <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `multiview::Bool`
  * `multiview_geometry_shader::Bool`
  * `multiview_tessellation_shader::Bool`
