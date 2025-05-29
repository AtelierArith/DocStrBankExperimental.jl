拡張: VK*AMD*texture*gather*bias_lod

引数:

  * `supports_texture_gather_lod_bias_amd::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTextureLODGatherFormatPropertiesAMD.html)

```julia
_TextureLODGatherFormatPropertiesAMD(
    supports_texture_gather_lod_bias_amd::Bool;
    next
) -> Vulkan._TextureLODGatherFormatPropertiesAMD

```
