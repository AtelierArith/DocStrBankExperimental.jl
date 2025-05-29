VkPhysicalDeviceFragmentShaderInterlockFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*fragment*shader*interlock

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShaderInterlockFeaturesEXT.html)

```julia
struct PhysicalDeviceFragmentShaderInterlockFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fragment_shader_sample_interlock::Bool`
  * `fragment_shader_pixel_interlock::Bool`
  * `fragment_shader_shading_rate_interlock::Bool`
