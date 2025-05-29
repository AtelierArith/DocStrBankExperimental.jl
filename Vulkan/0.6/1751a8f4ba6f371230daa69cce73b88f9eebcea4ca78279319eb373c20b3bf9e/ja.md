拡張: VK*EXT*image*compression*control

引数:

  * `image_compression_control::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageCompressionControlFeaturesEXT.html)

```julia
_PhysicalDeviceImageCompressionControlFeaturesEXT(
    image_compression_control::Bool;
    next
) -> Vulkan._PhysicalDeviceImageCompressionControlFeaturesEXT

```
