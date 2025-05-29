Arguments:

  * `data_size::UInt32`
  * `data::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSetInlineUniformBlock.html)

```julia
WriteDescriptorSetInlineUniformBlock(
    data_size::Integer,
    data::Ptr{Nothing};
    next
) -> Vulkan.WriteDescriptorSetInlineUniformBlock

```
