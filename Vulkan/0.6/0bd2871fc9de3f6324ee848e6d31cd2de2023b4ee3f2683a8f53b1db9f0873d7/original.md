Extension: VK_EXT_fragment_shader_interlock

Arguments:

  * `fragment_shader_sample_interlock::Bool`
  * `fragment_shader_pixel_interlock::Bool`
  * `fragment_shader_shading_rate_interlock::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShaderInterlockFeaturesEXT.html)

```julia
PhysicalDeviceFragmentShaderInterlockFeaturesEXT(
    fragment_shader_sample_interlock::Bool,
    fragment_shader_pixel_interlock::Bool,
    fragment_shader_shading_rate_interlock::Bool;
    next
) -> Vulkan.PhysicalDeviceFragmentShaderInterlockFeaturesEXT

```
