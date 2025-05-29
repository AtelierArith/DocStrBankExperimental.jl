返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `allocate_info::CommandBufferAllocateInfo` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateCommandBuffers.html)

```julia
allocate_command_buffers(
    device,
    allocate_info::Vulkan.CommandBufferAllocateInfo
) -> ResultTypes.Result{Vector{Vulkan.CommandBuffer}, Vulkan.VulkanError}

```
