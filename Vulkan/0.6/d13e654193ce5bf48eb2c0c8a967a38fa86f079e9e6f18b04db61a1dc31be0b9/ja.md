戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `command_buffer::CommandBuffer` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEndCommandBuffer.html)

```julia
end_command_buffer(
    command_buffer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
