引数:

  * `storage_buffer_8_bit_access::Bool`
  * `uniform_and_storage_buffer_8_bit_access::Bool`
  * `storage_push_constant_8::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevice8BitStorageFeatures.html)

```julia
_PhysicalDevice8BitStorageFeatures(
    storage_buffer_8_bit_access::Bool,
    uniform_and_storage_buffer_8_bit_access::Bool,
    storage_push_constant_8::Bool;
    next
) -> Vulkan._PhysicalDevice8BitStorageFeatures

```
