拡張: VK*EXT*opacity_micromap

引数:

  * `version_data::Vector{UInt8}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapVersionInfoEXT.html)

```julia
_MicromapVersionInfoEXT(
    version_data::AbstractArray;
    next
) -> Vulkan._MicromapVersionInfoEXT

```
