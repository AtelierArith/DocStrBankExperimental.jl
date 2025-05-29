Extension: VK_KHR_synchronization2

Arguments:

  * `checkpoint_execution_stage_mask::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointProperties2NV.html)

```julia
QueueFamilyCheckpointProperties2NV(
    checkpoint_execution_stage_mask::Integer;
    next
) -> Vulkan.QueueFamilyCheckpointProperties2NV

```
