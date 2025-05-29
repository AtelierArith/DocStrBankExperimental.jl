引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `linear_tiling_features::UInt64`: デフォルトは `0`
  * `optimal_tiling_features::UInt64`: デフォルトは `0`
  * `buffer_features::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFormatProperties3.html)

```julia
_FormatProperties3(
;
    next,
    linear_tiling_features,
    optimal_tiling_features,
    buffer_features
) -> Vulkan._FormatProperties3

```
