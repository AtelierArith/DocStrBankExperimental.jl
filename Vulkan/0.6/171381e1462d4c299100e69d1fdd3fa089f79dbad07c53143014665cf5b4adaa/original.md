Extension: VK_EXT_device_address_binding_report

Arguments:

  * `report_address_binding::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceAddressBindingReportFeaturesEXT.html)

```julia
_PhysicalDeviceAddressBindingReportFeaturesEXT(
    report_address_binding::Bool;
    next
) -> Vulkan._PhysicalDeviceAddressBindingReportFeaturesEXT

```
