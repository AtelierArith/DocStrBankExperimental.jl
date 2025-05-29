VkMicromapBuildInfoEXTの高レベルラッパー。

拡張: VK*EXT*opacity_micromap

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

```julia
struct MicromapBuildInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.MicromapTypeEXT`
  * `flags::Vulkan.BuildMicromapFlagEXT`
  * `mode::Vulkan.BuildMicromapModeEXT`
  * `dst_micromap::Union{Ptr{Nothing}, Vulkan.MicromapEXT}`
  * `usage_counts::Union{Ptr{Nothing}, Vector{Vulkan.MicromapUsageEXT}}`
  * `usage_counts_2::Union{Ptr{Nothing}, Vector{Vulkan.MicromapUsageEXT}}`
  * `data::Vulkan.DeviceOrHostAddressConstKHR`
  * `scratch_data::Vulkan.DeviceOrHostAddressKHR`
  * `triangle_array::Vulkan.DeviceOrHostAddressConstKHR`
  * `triangle_array_stride::UInt64`
