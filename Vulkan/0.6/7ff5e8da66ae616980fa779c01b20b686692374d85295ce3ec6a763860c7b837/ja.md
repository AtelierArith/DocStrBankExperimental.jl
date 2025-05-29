VkDeviceGroupSubmitInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupSubmitInfo.html)

```julia
struct DeviceGroupSubmitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `wait_semaphore_device_indices::Vector{UInt32}`
  * `command_buffer_device_masks::Vector{UInt32}`
  * `signal_semaphore_device_indices::Vector{UInt32}`
