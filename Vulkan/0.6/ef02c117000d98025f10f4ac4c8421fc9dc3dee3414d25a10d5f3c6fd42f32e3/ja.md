拡張: VK*EXT*vertex*input*dynamic_state

引数:

  * `location::UInt32`
  * `binding::UInt32`
  * `format::Format`
  * `offset::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputAttributeDescription2EXT.html)

```julia
_VertexInputAttributeDescription2EXT(
    location::Integer,
    binding::Integer,
    format::Vulkan.Format,
    offset::Integer;
    next
) -> Vulkan._VertexInputAttributeDescription2EXT

```
