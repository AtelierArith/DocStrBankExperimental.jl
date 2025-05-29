拡張: VK*KHR*pipeline*executable*properties

引数:

  * `name::String`
  * `description::String`
  * `format::PipelineExecutableStatisticFormatKHR`
  * `value::PipelineExecutableStatisticValueKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableStatisticKHR.html)

```julia
PipelineExecutableStatisticKHR(
    name::AbstractString,
    description::AbstractString,
    format::Vulkan.PipelineExecutableStatisticFormatKHR,
    value::Vulkan.PipelineExecutableStatisticValueKHR;
    next
) -> Vulkan.PipelineExecutableStatisticKHR

```
