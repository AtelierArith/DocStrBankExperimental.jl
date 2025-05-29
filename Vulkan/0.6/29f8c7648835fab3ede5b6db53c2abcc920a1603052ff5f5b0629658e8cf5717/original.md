Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `begin_info::CommandBufferBeginInfo`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBeginCommandBuffer.html)

```julia
begin_command_buffer(
    command_buffer,
    begin_info::Vulkan.CommandBufferBeginInfo
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
