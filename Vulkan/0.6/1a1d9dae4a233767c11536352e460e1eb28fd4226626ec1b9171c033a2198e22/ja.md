戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::BufferViewCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBufferView.html)

```julia
create_buffer_view(
    device,
    create_info::Vulkan.BufferViewCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.BufferView, Vulkan.VulkanError}

```
