Arguments:

  * `storage_buffer_16_bit_access::Bool`
  * `uniform_and_storage_buffer_16_bit_access::Bool`
  * `storage_push_constant_16::Bool`
  * `storage_input_output_16::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevice16BitStorageFeatures.html)

```julia
_PhysicalDevice16BitStorageFeatures(
    storage_buffer_16_bit_access::Bool,
    uniform_and_storage_buffer_16_bit_access::Bool,
    storage_push_constant_16::Bool,
    storage_input_output_16::Bool;
    next
) -> Vulkan._PhysicalDevice16BitStorageFeatures

```
