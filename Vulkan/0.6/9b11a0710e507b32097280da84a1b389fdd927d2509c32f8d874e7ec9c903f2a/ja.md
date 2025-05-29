拡張: VK*NVX*binary_import

引数:

  * `_module::CuModuleNVX`
  * `name::String`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuFunctionCreateInfoNVX.html)

```julia
CuFunctionCreateInfoNVX(
    _module::Vulkan.CuModuleNVX,
    name::AbstractString;
    next
) -> Vulkan.CuFunctionCreateInfoNVX

```
