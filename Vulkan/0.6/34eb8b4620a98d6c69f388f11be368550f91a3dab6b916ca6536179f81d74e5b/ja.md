拡張: VK*EXT*debug_utils

引数:

  * `instance::Instance`
  * `messenger::DebugUtilsMessengerEXT` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDebugUtilsMessengerEXT.html)

```julia
destroy_debug_utils_messenger_ext(
    instance,
    messenger;
    allocator
)

```
