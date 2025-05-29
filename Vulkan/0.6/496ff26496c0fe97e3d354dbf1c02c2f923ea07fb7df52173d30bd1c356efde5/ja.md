VkPhysicalDeviceBufferDeviceAddressFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*buffer*device*address

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBufferDeviceAddressFeaturesEXT.html)

```julia
struct PhysicalDeviceBufferDeviceAddressFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `buffer_device_address::Bool`
  * `buffer_device_address_capture_replay::Bool`
  * `buffer_device_address_multi_device::Bool`
