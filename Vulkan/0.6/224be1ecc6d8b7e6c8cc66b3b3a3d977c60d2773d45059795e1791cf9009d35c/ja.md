拡張: VK*KHR*performance_query

引数:

  * `name::String`
  * `category::String`
  * `description::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PerformanceCounterDescriptionFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterDescriptionKHR.html)

```julia
_PerformanceCounterDescriptionKHR(
    name::AbstractString,
    category::AbstractString,
    description::AbstractString;
    next,
    flags
)

```
