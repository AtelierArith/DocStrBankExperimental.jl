引数:

  * `semaphore_type::SemaphoreType`
  * `initial_value::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreTypeCreateInfo.html)

```julia
_SemaphoreTypeCreateInfo(
    semaphore_type::Vulkan.SemaphoreType,
    initial_value::Integer;
    next
) -> Vulkan._SemaphoreTypeCreateInfo

```
