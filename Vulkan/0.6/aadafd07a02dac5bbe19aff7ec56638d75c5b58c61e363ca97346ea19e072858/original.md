Arguments:

  * `device::Device`
  * `heap_index::UInt32`
  * `local_device_index::UInt32`
  * `remote_device_index::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceGroupPeerMemoryFeatures.html)

```julia
get_device_group_peer_memory_features(
    device,
    heap_index::Integer,
    local_device_index::Integer,
    remote_device_index::Integer
) -> Vulkan.PeerMemoryFeatureFlag

```
