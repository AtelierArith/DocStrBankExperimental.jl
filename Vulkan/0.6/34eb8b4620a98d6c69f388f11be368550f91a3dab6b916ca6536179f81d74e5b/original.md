Extension: VK_EXT_debug_utils

Arguments:

  * `instance::Instance`
  * `messenger::DebugUtilsMessengerEXT` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDebugUtilsMessengerEXT.html)

```julia
destroy_debug_utils_messenger_ext(
    instance,
    messenger;
    allocator
)

```
