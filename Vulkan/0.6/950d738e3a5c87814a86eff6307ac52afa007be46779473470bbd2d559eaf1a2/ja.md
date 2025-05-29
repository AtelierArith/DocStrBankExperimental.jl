拡張機能: VK*EXT*device*memory*report

引数:

  * `flags::UInt32`
  * `pfn_user_callback::FunctionPtr`
  * `user_data::Ptr{Cvoid}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceDeviceMemoryReportCreateInfoEXT.html)

```julia
DeviceDeviceMemoryReportCreateInfoEXT(
    flags::Integer,
    pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction},
    user_data::Ptr{Nothing};
    next
) -> Vulkan.DeviceDeviceMemoryReportCreateInfoEXT

```
