Extension: VK_EXT_validation_cache

Arguments:

  * `initial_data::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `initial_data_size::UInt`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationCacheCreateInfoEXT.html)

```julia
ValidationCacheCreateInfoEXT(
    initial_data::Ptr{Nothing};
    next,
    flags,
    initial_data_size
) -> Vulkan.ValidationCacheCreateInfoEXT

```
