Extension: VK_KHR_performance_query

Arguments:

  * `name::String`
  * `category::String`
  * `description::String`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PerformanceCounterDescriptionFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterDescriptionKHR.html)

```julia
_PerformanceCounterDescriptionKHR(
    name::AbstractString,
    category::AbstractString,
    description::AbstractString;
    next,
    flags
)

```
