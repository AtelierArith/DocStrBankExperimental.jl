引数:

  * `variable_pointers_storage_buffer::Bool`
  * `variable_pointers::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVariablePointersFeatures.html)

```julia
_PhysicalDeviceVariablePointersFeatures(
    variable_pointers_storage_buffer::Bool,
    variable_pointers::Bool;
    next
) -> Vulkan._PhysicalDeviceVariablePointersFeatures

```
