拡張: VK*EXT*device_fault

引数:

  * `device_fault::Bool`
  * `device_fault_vendor_binary::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFaultFeaturesEXT.html)

```julia
_PhysicalDeviceFaultFeaturesEXT(
    device_fault::Bool,
    device_fault_vendor_binary::Bool;
    next
) -> Vulkan._PhysicalDeviceFaultFeaturesEXT

```
