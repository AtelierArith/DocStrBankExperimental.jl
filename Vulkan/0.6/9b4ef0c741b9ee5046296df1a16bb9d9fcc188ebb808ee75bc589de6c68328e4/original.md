Extension: VK_KHR_shader_clock

Arguments:

  * `shader_subgroup_clock::Bool`
  * `shader_device_clock::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderClockFeaturesKHR.html)

```julia
PhysicalDeviceShaderClockFeaturesKHR(
    shader_subgroup_clock::Bool,
    shader_device_clock::Bool;
    next
) -> Vulkan.PhysicalDeviceShaderClockFeaturesKHR

```
