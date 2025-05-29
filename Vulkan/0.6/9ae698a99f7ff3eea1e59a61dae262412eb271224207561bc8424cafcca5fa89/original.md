Extension: VK_GOOGLE_display_timing

Arguments:

  * `present_id::UInt32`
  * `desired_present_time::UInt64`
  * `actual_present_time::UInt64`
  * `earliest_present_time::UInt64`
  * `present_margin::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPastPresentationTimingGOOGLE.html)

```julia
_PastPresentationTimingGOOGLE(
    present_id::Integer,
    desired_present_time::Integer,
    actual_present_time::Integer,
    earliest_present_time::Integer,
    present_margin::Integer
) -> Vulkan._PastPresentationTimingGOOGLE

```
