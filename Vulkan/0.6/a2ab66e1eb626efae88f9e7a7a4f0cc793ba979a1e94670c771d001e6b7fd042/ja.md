拡張: VK*EXT*vertex*input*dynamic_state

引数:

  * `binding::UInt32`
  * `stride::UInt32`
  * `input_rate::VertexInputRate`
  * `divisor::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputBindingDescription2EXT.html)

```julia
_VertexInputBindingDescription2EXT(
    binding::Integer,
    stride::Integer,
    input_rate::Vulkan.VertexInputRate,
    divisor::Integer;
    next
) -> Vulkan._VertexInputBindingDescription2EXT

```
