戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `flags::CommandBufferResetFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkResetCommandBuffer.html)

```julia
reset_command_buffer(
    command_buffer;
    flags
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
