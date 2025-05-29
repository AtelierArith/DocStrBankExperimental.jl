拡張: VK*NVX*image*view*handle

引数:

  * `device_address::UInt64`
  * `size::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewAddressPropertiesNVX.html)

```julia
_ImageViewAddressPropertiesNVX(
    device_address::Integer,
    size::Integer;
    next
) -> Vulkan._ImageViewAddressPropertiesNVX

```
