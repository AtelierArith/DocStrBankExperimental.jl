Arguments:

  * `variable_pointers_storage_buffer::Bool`
  * `variable_pointers::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVariablePointersFeatures.html)

```julia
_PhysicalDeviceVariablePointersFeatures(
    variable_pointers_storage_buffer::Bool,
    variable_pointers::Bool;
    next
) -> Vulkan._PhysicalDeviceVariablePointersFeatures

```
