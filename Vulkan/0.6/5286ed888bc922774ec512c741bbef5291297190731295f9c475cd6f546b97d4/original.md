Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::RenderPassCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass.html)

```julia
create_render_pass(
    device,
    create_info::Vulkan.RenderPassCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
