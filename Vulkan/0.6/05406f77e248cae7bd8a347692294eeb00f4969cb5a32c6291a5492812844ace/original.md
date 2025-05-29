Extension: VK_SEC_amigo_profiling

Arguments:

  * `first_draw_timestamp::UInt64`
  * `swap_buffer_timestamp::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAmigoProfilingSubmitInfoSEC.html)

```julia
AmigoProfilingSubmitInfoSEC(
    first_draw_timestamp::Integer,
    swap_buffer_timestamp::Integer;
    next
) -> Vulkan.AmigoProfilingSubmitInfoSEC

```
