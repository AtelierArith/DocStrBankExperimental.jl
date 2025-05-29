Extension: VK_NV_device_generated_commands

Arguments:

  * `device::Device`
  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{_IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateIndirectCommandsLayoutNV.html)

```julia
IndirectCommandsLayoutNV(
    device,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray{Vulkan._IndirectCommandsLayoutTokenNV},
    stream_strides::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.IndirectCommandsLayoutNV

```
