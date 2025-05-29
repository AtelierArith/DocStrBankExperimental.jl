拡張: VK*NV*device*generated*commands

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `pipeline_bind_point::PipelineBindPoint`
  * `tokens::Vector{IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::IndirectCommandsLayoutUsageFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateIndirectCommandsLayoutNV.html)

```julia
create_indirect_commands_layout_nv(
    device,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    tokens::AbstractArray,
    stream_strides::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.IndirectCommandsLayoutNV, Vulkan.VulkanError}

```
