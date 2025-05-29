Extension: VK_EXT_extended_dynamic_state2

Arguments:

  * `extended_dynamic_state_2::Bool`
  * `extended_dynamic_state_2_logic_op::Bool`
  * `extended_dynamic_state_2_patch_control_points::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExtendedDynamicState2FeaturesEXT.html)

```julia
_PhysicalDeviceExtendedDynamicState2FeaturesEXT(
    extended_dynamic_state_2::Bool,
    extended_dynamic_state_2_logic_op::Bool,
    extended_dynamic_state_2_patch_control_points::Bool;
    next
) -> Vulkan._PhysicalDeviceExtendedDynamicState2FeaturesEXT

```
