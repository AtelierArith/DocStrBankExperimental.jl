Extension: VK_KHR_synchronization2

Arguments:

  * `checkpoint_execution_stage_mask::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointProperties2NV.html)

```julia
_QueueFamilyCheckpointProperties2NV(
    checkpoint_execution_stage_mask::Integer;
    next
) -> Vulkan._QueueFamilyCheckpointProperties2NV

```
