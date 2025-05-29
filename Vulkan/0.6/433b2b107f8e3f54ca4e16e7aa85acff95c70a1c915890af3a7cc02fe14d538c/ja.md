VkPhysicalDevicePCIBusInfoPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*pci*bus*info

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePCIBusInfoPropertiesEXT.html)

```julia
struct PhysicalDevicePCIBusInfoPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pci_domain::UInt32`
  * `pci_bus::UInt32`
  * `pci_device::UInt32`
  * `pci_function::UInt32`
