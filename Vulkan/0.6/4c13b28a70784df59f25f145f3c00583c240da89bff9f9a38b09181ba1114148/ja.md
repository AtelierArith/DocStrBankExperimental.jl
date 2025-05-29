拡張: VK*KHR*pipeline*executable*properties

引数:

  * `name::String`
  * `description::String`
  * `is_text::Bool`
  * `data_size::UInt`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInternalRepresentationKHR.html)

```julia
_PipelineExecutableInternalRepresentationKHR(
    name::AbstractString,
    description::AbstractString,
    is_text::Bool,
    data_size::Integer;
    next,
    data
)

```
