引数:

  * `buffer_device_address::Bool`
  * `buffer_device_address_capture_replay::Bool`
  * `buffer_device_address_multi_device::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceBufferDeviceAddressFeatures.html)

```julia
_PhysicalDeviceBufferDeviceAddressFeatures(
    buffer_device_address::Bool,
    buffer_device_address_capture_replay::Bool,
    buffer_device_address_multi_device::Bool;
    next
) -> Vulkan._PhysicalDeviceBufferDeviceAddressFeatures

```
