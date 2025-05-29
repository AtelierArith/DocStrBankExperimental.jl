Extension: VK_AMD_texture_gather_bias_lod

Arguments:

  * `supports_texture_gather_lod_bias_amd::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTextureLODGatherFormatPropertiesAMD.html)

```julia
_TextureLODGatherFormatPropertiesAMD(
    supports_texture_gather_lod_bias_amd::Bool;
    next
) -> Vulkan._TextureLODGatherFormatPropertiesAMD

```
