戻り値のコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `begin_info::_CommandBufferBeginInfo`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBeginCommandBuffer.html)

```julia
_begin_command_buffer(
    command_buffer,
    begin_info::Vulkan._CommandBufferBeginInfo
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
