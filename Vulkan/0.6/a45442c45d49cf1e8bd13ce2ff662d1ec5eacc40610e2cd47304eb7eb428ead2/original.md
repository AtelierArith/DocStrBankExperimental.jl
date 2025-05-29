Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `create_info::_ImageCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImage.html)

```julia
_create_image(
    device,
    create_info::Vulkan._ImageCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Image, Vulkan.VulkanError}

```
