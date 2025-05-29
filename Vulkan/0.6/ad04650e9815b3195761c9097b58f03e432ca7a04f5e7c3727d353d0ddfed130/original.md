High-level wrapper for VkPhysicalDeviceFragmentShaderInterlockFeaturesEXT.

Extension: VK_EXT_fragment_shader_interlock

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShaderInterlockFeaturesEXT.html)

```julia
struct PhysicalDeviceFragmentShaderInterlockFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fragment_shader_sample_interlock::Bool`
  * `fragment_shader_pixel_interlock::Bool`
  * `fragment_shader_shading_rate_interlock::Bool`
