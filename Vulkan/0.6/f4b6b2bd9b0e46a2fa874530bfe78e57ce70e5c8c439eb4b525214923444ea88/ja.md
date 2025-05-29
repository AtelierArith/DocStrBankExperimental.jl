拡張: VK*KHR*synchronization2

引数:

  * `checkpoint_execution_stage_mask::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointProperties2NV.html)

```julia
_QueueFamilyCheckpointProperties2NV(
    checkpoint_execution_stage_mask::Integer;
    next
) -> Vulkan._QueueFamilyCheckpointProperties2NV

```
