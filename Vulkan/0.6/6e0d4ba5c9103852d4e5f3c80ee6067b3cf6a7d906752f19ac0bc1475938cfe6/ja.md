拡張: VK*EXT*opacity_micromap

引数:

  * `version_data::Vector{UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapVersionInfoEXT.html)

```julia
MicromapVersionInfoEXT(
    version_data::AbstractArray;
    next
) -> Vulkan.MicromapVersionInfoEXT

```
