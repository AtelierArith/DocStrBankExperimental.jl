Extension: VK_EXT_device_fault

Arguments:

  * `device_fault::Bool`
  * `device_fault_vendor_binary::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFaultFeaturesEXT.html)

```julia
_PhysicalDeviceFaultFeaturesEXT(
    device_fault::Bool,
    device_fault_vendor_binary::Bool;
    next
) -> Vulkan._PhysicalDeviceFaultFeaturesEXT

```
