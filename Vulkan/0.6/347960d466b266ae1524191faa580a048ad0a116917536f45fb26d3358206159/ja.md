拡張: VK*EXT*validation_cache

引数:

  * `initial_data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `initial_data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationCacheCreateInfoEXT.html)

```julia
_ValidationCacheCreateInfoEXT(
    initial_data::Ptr{Nothing};
    next,
    flags,
    initial_data_size
) -> Vulkan._ValidationCacheCreateInfoEXT

```
