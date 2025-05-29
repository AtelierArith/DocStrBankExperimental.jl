引数:

  * `protected_no_fault::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProtectedMemoryProperties.html)

```julia
_PhysicalDeviceProtectedMemoryProperties(
    protected_no_fault::Bool;
    next
) -> Vulkan._PhysicalDeviceProtectedMemoryProperties

```
