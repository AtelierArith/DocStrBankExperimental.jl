引数:

  * `protected_memory::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProtectedMemoryFeatures.html)

```julia
_PhysicalDeviceProtectedMemoryFeatures(
    protected_memory::Bool;
    next
) -> Vulkan._PhysicalDeviceProtectedMemoryFeatures

```
