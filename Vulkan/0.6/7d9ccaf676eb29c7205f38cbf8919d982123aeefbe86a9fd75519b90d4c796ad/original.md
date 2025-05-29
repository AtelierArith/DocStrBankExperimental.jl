Extension: VK_EXT_opacity_micromap

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `create_info::MicromapCreateInfoEXT`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateMicromapEXT.html)

```julia
create_micromap_ext(
    device,
    create_info::Vulkan.MicromapCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.MicromapEXT, Vulkan.VulkanError}

```
