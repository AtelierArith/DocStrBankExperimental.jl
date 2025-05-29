戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::FramebufferCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFramebuffer.html)

```julia
create_framebuffer(
    device,
    create_info::Vulkan.FramebufferCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Framebuffer, Vulkan.VulkanError}

```
