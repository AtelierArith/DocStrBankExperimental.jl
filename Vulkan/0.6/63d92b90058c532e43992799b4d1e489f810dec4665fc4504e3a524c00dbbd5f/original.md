Extension: VK_EXT_pci_bus_info

Arguments:

  * `pci_domain::UInt32`
  * `pci_bus::UInt32`
  * `pci_device::UInt32`
  * `pci_function::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePCIBusInfoPropertiesEXT.html)

```julia
_PhysicalDevicePCIBusInfoPropertiesEXT(
    pci_domain::Integer,
    pci_bus::Integer,
    pci_device::Integer,
    pci_function::Integer;
    next
) -> Vulkan._PhysicalDevicePCIBusInfoPropertiesEXT

```
