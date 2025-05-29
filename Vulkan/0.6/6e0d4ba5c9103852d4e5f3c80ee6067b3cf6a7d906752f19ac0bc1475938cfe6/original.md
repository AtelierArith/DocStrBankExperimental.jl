Extension: VK_EXT_opacity_micromap

Arguments:

  * `version_data::Vector{UInt8}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapVersionInfoEXT.html)

```julia
MicromapVersionInfoEXT(
    version_data::AbstractArray;
    next
) -> Vulkan.MicromapVersionInfoEXT

```
