拡張: VK*SEC*amigo_profiling

引数:

  * `first_draw_timestamp::UInt64`
  * `swap_buffer_timestamp::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAmigoProfilingSubmitInfoSEC.html)

```julia
AmigoProfilingSubmitInfoSEC(
    first_draw_timestamp::Integer,
    swap_buffer_timestamp::Integer;
    next
) -> Vulkan.AmigoProfilingSubmitInfoSEC

```
