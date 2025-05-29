High-level wrapper for VkPhysicalDevicePCIBusInfoPropertiesEXT.

Extension: VK_EXT_pci_bus_info

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePCIBusInfoPropertiesEXT.html)

```julia
struct PhysicalDevicePCIBusInfoPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pci_domain::UInt32`
  * `pci_bus::UInt32`
  * `pci_device::UInt32`
  * `pci_function::UInt32`
