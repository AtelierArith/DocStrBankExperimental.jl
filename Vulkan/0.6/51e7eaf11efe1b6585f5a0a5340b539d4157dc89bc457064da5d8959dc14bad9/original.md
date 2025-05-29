Arguments:

  * `semaphore_type::SemaphoreType`
  * `initial_value::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreTypeCreateInfo.html)

```julia
SemaphoreTypeCreateInfo(
    semaphore_type::Vulkan.SemaphoreType,
    initial_value::Integer;
    next
) -> Vulkan.SemaphoreTypeCreateInfo

```
