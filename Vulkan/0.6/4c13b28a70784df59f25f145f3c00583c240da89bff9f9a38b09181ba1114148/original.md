Extension: VK_KHR_pipeline_executable_properties

Arguments:

  * `name::String`
  * `description::String`
  * `is_text::Bool`
  * `data_size::UInt`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInternalRepresentationKHR.html)

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
