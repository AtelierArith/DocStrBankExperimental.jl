返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::BufferCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateBuffer.html)

```julia
create_buffer(
    device,
    create_info::Vulkan.BufferCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Buffer, Vulkan.VulkanError}

```
