Extension: VK_NVX_binary_import

Arguments:

  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuModuleCreateInfoNVX.html)

```julia
_CuModuleCreateInfoNVX(
    data_size::Integer,
    data::Ptr{Nothing};
    next
) -> Vulkan._CuModuleCreateInfoNVX

```
