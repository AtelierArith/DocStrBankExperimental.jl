戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::RenderPassCreateInfo2`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

```julia
create_render_pass_2(
    device,
    create_info::Vulkan.RenderPassCreateInfo2;
    allocator
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
