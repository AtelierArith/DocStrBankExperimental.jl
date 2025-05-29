拡張: VK*NVX*binary_import

引数:

  * `_module::CuModuleNVX`
  * `name::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuFunctionCreateInfoNVX.html)

```julia
_CuFunctionCreateInfoNVX(
    _module,
    name::AbstractString;
    next
) -> Vulkan._CuFunctionCreateInfoNVX

```
