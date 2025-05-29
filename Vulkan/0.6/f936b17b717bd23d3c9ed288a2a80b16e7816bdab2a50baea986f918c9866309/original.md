Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `allocate_info::_CommandBufferAllocateInfo` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateCommandBuffers.html)

```julia
_allocate_command_buffers(
    device,
    allocate_info::Vulkan._CommandBufferAllocateInfo
) -> ResultTypes.Result{Vector{Vulkan.CommandBuffer}, Vulkan.VulkanError}

```
