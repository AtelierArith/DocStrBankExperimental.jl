拡張: VK*EXT*debug_report

引数:

  * `pfn_callback::FunctionPtr`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DebugReportFlagEXT`: デフォルトは `0`
  * `user_data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugReportCallbackCreateInfoEXT.html)

```julia
_DebugReportCallbackCreateInfoEXT(
    pfn_callback::Union{Ptr{Nothing}, Base.CFunction};
    next,
    flags,
    user_data
) -> Vulkan._DebugReportCallbackCreateInfoEXT

```
