Extension: VK_NV_device_generated_commands

Arguments:

  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutCreateInfoNV.html)

```julia
IndirectCommandsLayoutCreateInfoNV(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray,
    stream_strides::AbstractArray;
    next,
    flags
) -> Vulkan.IndirectCommandsLayoutCreateInfoNV

```
