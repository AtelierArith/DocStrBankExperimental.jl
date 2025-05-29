Extension: VK_KHR_synchronization2

Arguments:

  * `stage::UInt64`
  * `checkpoint_marker::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointData2NV.html)

```julia
CheckpointData2NV(
    stage::Integer,
    checkpoint_marker::Ptr{Nothing};
    next
) -> Vulkan.CheckpointData2NV

```
