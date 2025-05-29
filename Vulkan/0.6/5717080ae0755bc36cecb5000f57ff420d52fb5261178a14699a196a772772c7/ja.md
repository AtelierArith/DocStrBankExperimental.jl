VkCheckpointData2NVの高レベルラッパー。

拡張: VK*KHR*synchronization2

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointData2NV.html)

```julia
struct CheckpointData2NV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stage::UInt64`
  * `checkpoint_marker::Ptr{Nothing}`
