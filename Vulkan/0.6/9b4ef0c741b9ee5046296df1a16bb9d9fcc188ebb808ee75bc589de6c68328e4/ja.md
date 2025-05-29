拡張: VK*KHR*shader_clock

引数:

  * `shader_subgroup_clock::Bool`
  * `shader_device_clock::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderClockFeaturesKHR.html)

```julia
PhysicalDeviceShaderClockFeaturesKHR(
    shader_subgroup_clock::Bool,
    shader_device_clock::Bool;
    next
) -> Vulkan.PhysicalDeviceShaderClockFeaturesKHR

```
