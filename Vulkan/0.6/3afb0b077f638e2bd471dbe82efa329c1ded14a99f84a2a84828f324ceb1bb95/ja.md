拡張: VK*NVX*binary_import

引数:

  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuModuleCreateInfoNVX.html)

```julia
_CuModuleCreateInfoNVX(
    data_size::Integer,
    data::Ptr{Nothing};
    next
) -> Vulkan._CuModuleCreateInfoNVX

```
