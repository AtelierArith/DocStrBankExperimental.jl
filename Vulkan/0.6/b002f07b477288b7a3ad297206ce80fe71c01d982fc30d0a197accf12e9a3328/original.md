Extension: VK_NV_fragment_shading_rate_enums

Arguments:

  * `fragment_shading_rate_enums::Bool`
  * `supersample_fragment_shading_rates::Bool`
  * `no_invocation_fragment_shading_rates::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentShadingRateEnumsFeaturesNV.html)

```julia
_PhysicalDeviceFragmentShadingRateEnumsFeaturesNV(
    fragment_shading_rate_enums::Bool,
    supersample_fragment_shading_rates::Bool,
    no_invocation_fragment_shading_rates::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentShadingRateEnumsFeaturesNV

```
