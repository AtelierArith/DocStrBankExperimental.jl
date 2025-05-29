拡張: VK*EXT*fragment*shader*interlock

引数:

  * `fragment_shader_sample_interlock::Bool`
  * `fragment_shader_pixel_interlock::Bool`
  * `fragment_shader_shading_rate_interlock::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShaderInterlockFeaturesEXT.html)

```julia
_PhysicalDeviceFragmentShaderInterlockFeaturesEXT(
    fragment_shader_sample_interlock::Bool,
    fragment_shader_pixel_interlock::Bool,
    fragment_shader_shading_rate_interlock::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentShaderInterlockFeaturesEXT

```
