拡張: VK*KHR*synchronization2

引数:

  * `stage::UInt64`
  * `checkpoint_marker::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointData2NV.html)

```julia
_CheckpointData2NV(
    stage::Integer,
    checkpoint_marker::Ptr{Nothing};
    next
) -> Vulkan._CheckpointData2NV

```
