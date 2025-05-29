Extension: VK_EXT_calibrated_timestamps

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `timestamp_infos::Vector{CalibratedTimestampInfoEXT}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetCalibratedTimestampsEXT.html)

```julia
get_calibrated_timestamps_ext(
    device,
    timestamp_infos::AbstractArray
) -> ResultTypes.Result{Tuple{Vector{UInt64}, UInt64}, Vulkan.VulkanError}

```
