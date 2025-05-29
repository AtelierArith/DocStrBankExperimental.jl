拡張: VK*KHR*pipeline*executable*properties

引数:

  * `pipeline::Pipeline`
  * `executable_index::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInfoKHR.html)

```julia
PipelineExecutableInfoKHR(
    pipeline::Vulkan.Pipeline,
    executable_index::Integer;
    next
) -> Vulkan.PipelineExecutableInfoKHR

```
