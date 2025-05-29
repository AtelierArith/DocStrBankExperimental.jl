Arguments:

  * `storage_buffer_8_bit_access::Bool`
  * `uniform_and_storage_buffer_8_bit_access::Bool`
  * `storage_push_constant_8::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevice8BitStorageFeatures.html)

```julia
PhysicalDevice8BitStorageFeatures(
    storage_buffer_8_bit_access::Bool,
    uniform_and_storage_buffer_8_bit_access::Bool,
    storage_push_constant_8::Bool;
    next
) -> Vulkan.PhysicalDevice8BitStorageFeatures

```
