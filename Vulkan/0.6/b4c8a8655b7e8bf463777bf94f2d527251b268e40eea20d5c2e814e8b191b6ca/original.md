Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_FramebufferCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFramebuffer.html)

```julia
_create_framebuffer(
    device,
    create_info::Vulkan._FramebufferCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Framebuffer, Vulkan.VulkanError}

```
