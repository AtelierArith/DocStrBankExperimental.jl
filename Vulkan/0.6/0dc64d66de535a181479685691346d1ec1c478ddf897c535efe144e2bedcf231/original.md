Extension: VK_EXT_validation_cache

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::ValidationCacheCreateInfoEXT`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateValidationCacheEXT.html)

```julia
create_validation_cache_ext(
    device,
    create_info::Vulkan.ValidationCacheCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.ValidationCacheEXT, Vulkan.VulkanError}

```
