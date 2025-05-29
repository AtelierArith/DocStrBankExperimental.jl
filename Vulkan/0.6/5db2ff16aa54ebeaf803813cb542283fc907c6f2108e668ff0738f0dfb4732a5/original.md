Extension: VK_EXT_validation_cache

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_ValidationCacheCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateValidationCacheEXT.html)

```julia
_create_validation_cache_ext(
    device,
    create_info::Vulkan._ValidationCacheCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.ValidationCacheEXT, Vulkan.VulkanError}

```
