拡張: VK*EXT*device*address*binding_report

引数:

  * `report_address_binding::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceAddressBindingReportFeaturesEXT.html)

```julia
_PhysicalDeviceAddressBindingReportFeaturesEXT(
    report_address_binding::Bool;
    next
) -> Vulkan._PhysicalDeviceAddressBindingReportFeaturesEXT

```
