Extension: VK_EXT_calibrated_timestamps

Arguments:

  * `time_domain::TimeDomainEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCalibratedTimestampInfoEXT.html)

```julia
_CalibratedTimestampInfoEXT(
    time_domain::Vulkan.TimeDomainEXT;
    next
) -> Vulkan._CalibratedTimestampInfoEXT

```
