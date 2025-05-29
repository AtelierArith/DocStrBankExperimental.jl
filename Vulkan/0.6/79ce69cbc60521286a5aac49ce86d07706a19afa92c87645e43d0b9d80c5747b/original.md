Arguments:

  * `wait_semaphore_device_indices::Vector{UInt32}`
  * `command_buffer_device_masks::Vector{UInt32}`
  * `signal_semaphore_device_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupSubmitInfo.html)

```julia
_DeviceGroupSubmitInfo(
    wait_semaphore_device_indices::AbstractArray,
    command_buffer_device_masks::AbstractArray,
    signal_semaphore_device_indices::AbstractArray;
    next
) -> Vulkan._DeviceGroupSubmitInfo

```
