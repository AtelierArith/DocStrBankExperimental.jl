Extension: VK_NVX_binary_import

Arguments:

  * `_module::CuModuleNVX`
  * `name::String`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuFunctionCreateInfoNVX.html)

```julia
_CuFunctionCreateInfoNVX(
    _module,
    name::AbstractString;
    next
) -> Vulkan._CuFunctionCreateInfoNVX

```
