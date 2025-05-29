Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `flags::CommandBufferResetFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkResetCommandBuffer.html)

```julia
reset_command_buffer(
    command_buffer;
    flags
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
