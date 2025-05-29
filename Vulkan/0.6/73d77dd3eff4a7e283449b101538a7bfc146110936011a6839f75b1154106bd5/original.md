Extension: VK_NVX_binary_import

Arguments:

  * `data_size::UInt`
  * `data::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuModuleCreateInfoNVX.html)

```julia
CuModuleCreateInfoNVX(
    data_size::Integer,
    data::Ptr{Nothing};
    next
) -> Vulkan.CuModuleCreateInfoNVX

```
