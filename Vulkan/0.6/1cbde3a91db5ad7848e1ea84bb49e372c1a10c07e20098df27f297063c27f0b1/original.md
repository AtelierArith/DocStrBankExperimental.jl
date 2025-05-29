Extension: VK_EXT_opacity_micromap

Arguments:

  * `micromap_size::UInt64`
  * `build_scratch_size::UInt64`
  * `discardable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildSizesInfoEXT.html)

```julia
_MicromapBuildSizesInfoEXT(
    micromap_size::Integer,
    build_scratch_size::Integer,
    discardable::Bool;
    next
) -> Vulkan._MicromapBuildSizesInfoEXT

```
