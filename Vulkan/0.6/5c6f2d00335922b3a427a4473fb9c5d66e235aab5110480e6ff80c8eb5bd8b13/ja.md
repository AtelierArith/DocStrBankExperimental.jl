拡張: VK*KHR*synchronization2

引数:

  * `checkpoint_execution_stage_mask::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointProperties2NV.html)

```julia
QueueFamilyCheckpointProperties2NV(
    checkpoint_execution_stage_mask::Integer;
    next
) -> Vulkan.QueueFamilyCheckpointProperties2NV

```
