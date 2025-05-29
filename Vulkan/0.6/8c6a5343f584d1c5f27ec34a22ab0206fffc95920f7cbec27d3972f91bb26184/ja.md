VkCopyMemoryIndirectCommandNVの高レベルラッパー。

拡張: VK*NV*copy*memory*indirect

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryIndirectCommandNV.html)

```julia
struct CopyMemoryIndirectCommandNV <: Vulkan.HighLevelStruct
```

  * `src_address::UInt64`
  * `dst_address::UInt64`
  * `size::UInt64`
