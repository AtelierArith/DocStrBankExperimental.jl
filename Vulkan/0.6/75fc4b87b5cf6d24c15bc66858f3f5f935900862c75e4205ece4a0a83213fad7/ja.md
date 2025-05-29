VkPipelineExecutableInfoKHRの高レベルラッパー。

拡張: VK*KHR*pipeline*executable*properties

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInfoKHR.html)

```julia
struct PipelineExecutableInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pipeline::Vulkan.Pipeline`
  * `executable_index::UInt32`
