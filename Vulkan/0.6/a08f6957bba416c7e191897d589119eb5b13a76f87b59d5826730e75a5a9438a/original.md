Extension: VK_EXT_debug_utils

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `instance::Instance`
  * `create_info::_DebugUtilsMessengerCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugUtilsMessengerEXT.html)

```julia
_create_debug_utils_messenger_ext(
    instance,
    create_info::Vulkan._DebugUtilsMessengerCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.DebugUtilsMessengerEXT, Vulkan.VulkanError}

```
