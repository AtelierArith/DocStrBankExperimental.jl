Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `linear_tiling_features::UInt64`: defaults to `0`
  * `optimal_tiling_features::UInt64`: defaults to `0`
  * `buffer_features::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFormatProperties3.html)

```julia
_FormatProperties3(
;
    next,
    linear_tiling_features,
    optimal_tiling_features,
    buffer_features
) -> Vulkan._FormatProperties3

```
