Extension: VK_EXT_opacity_micromap

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `create_info::_MicromapCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
_create_micromap_ext(
    device,
    create_info::Vulkan._MicromapCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.MicromapEXT, Vulkan.VulkanError}

```
