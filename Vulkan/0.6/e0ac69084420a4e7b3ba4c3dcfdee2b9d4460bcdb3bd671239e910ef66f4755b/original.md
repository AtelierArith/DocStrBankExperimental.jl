Extension: VK_EXT_debug_report

Arguments:

  * `pfn_callback::FunctionPtr`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DebugReportFlagEXT`: defaults to `0`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugReportCallbackCreateInfoEXT.html)

```julia
_DebugReportCallbackCreateInfoEXT(
    pfn_callback::Union{Ptr{Nothing}, Base.CFunction};
    next,
    flags,
    user_data
) -> Vulkan._DebugReportCallbackCreateInfoEXT

```
