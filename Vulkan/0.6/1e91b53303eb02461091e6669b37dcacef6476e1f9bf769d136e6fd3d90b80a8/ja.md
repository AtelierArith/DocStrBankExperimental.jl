戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::_RenderPassCreateInfo`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass.html)

```julia
_create_render_pass(
    device,
    create_info::Vulkan._RenderPassCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
