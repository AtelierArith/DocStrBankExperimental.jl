返すコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `create_info::ImageCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImage.html)

```julia
create_image(
    device,
    create_info::Vulkan.ImageCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Image, Vulkan.VulkanError}

```
