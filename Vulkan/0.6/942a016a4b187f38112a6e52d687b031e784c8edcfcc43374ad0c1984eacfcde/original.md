Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_RenderPassCreateInfo2`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

```julia
_create_render_pass_2(
    device,
    create_info::Vulkan._RenderPassCreateInfo2;
    allocator
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
